<template>
    <div class="widget">
        <div class="rates">
            <h4>USD</h4>
            <div v-if="rates.loading">Загрузка...</div>
            <div v-else-if="rates.data" class="rate-value">
                {{ rates.data.USD.toFixed(2) }} ₽
            </div>
            <div v-else class="error">—</div>
        </div>

        <div class="rates">
            <h4>EUR</h4>
            <div v-if="rates.loading">Загрузка...</div>
            <div v-else-if="rates.data" class="rate-value">
                {{ rates.data.EUR.toFixed(2) }} ₽
            </div>
            <div v-else class="error">—</div>
        </div>

        <div class="rates">
            <h4>BTC</h4>
            <div v-if="rates.loading">Загрузка...</div>
            <div v-else-if="rates.data" class="rate-value">
                {{ rates.data.BTC.toFixed(2) }} ₽
            </div>
            <div v-else class="error">—</div>
        </div>
    </div>
</template>

<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const intervalId = ref<number | null>(null)

interface RatesData {
  USD: number
  EUR: number
  BTC: number
}

const rates = ref({
  loading: false,
  data: null as RatesData | null,
  error: ''
})

// Функция для получения курсов валют (используем бесплатный API)
async function fetchRates() {
  rates.value.loading = true
  try {
    const response = await fetch('https://api.exchangerate-api.com/v4/latest/RUB')
    
    if (!response.ok) throw new Error('Ошибка получения курсов')
    
    const data = await response.json()

    // Отдельный запрос для BTC
    const btcResponse = await fetch('https://api.coingecko.com/api/v3/simple/price?ids=bitcoin&vs_currencies=rub')
    const btcData = await btcResponse.json()
    
    rates.value.data = {
      USD: 1 / data.rates.USD,
      EUR: 1 / data.rates.EUR,
      BTC: btcData.bitcoin.rub,
    }
  } catch (error) {
    // Резервный вариант с другим API
    try {
      const response = await fetch('https://api.coingate.com/api/v2/rates/merchant/USD/RUB')
      const usdRate = await response.json()
      
      const eurResponse = await fetch('https://api.coingate.com/api/v2/rates/merchant/EUR/RUB')
      const eurRate = await eurResponse.json()
      
      const btcResponse = await fetch('https://api.coingate.com/api/v2/rates/merchant/BTC/RUB')
      const btcRate = await btcResponse.json()
      
      rates.value.data = {
        USD: usdRate,
        EUR: eurRate,
        BTC: btcRate
      }
    } catch (backupError) {
      rates.value.error = 'Не удалось загрузить курсы'
      console.error('Rates error:', backupError)
    }
  } finally {
    rates.value.loading = false
  }
}

onMounted(() => {
  fetchRates()
  // Обновляем данные каждые 10 минут
  intervalId.value = setInterval(fetchRates, 10 * 60 * 1000)
})

onUnmounted(() => {
  if (intervalId.value) {
    clearInterval(intervalId.value)
    intervalId.value = null
  }
})
</script>

<style scoped>
.widget{
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
}
.rates{
    margin-left: 20px;
}
</style>
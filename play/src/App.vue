<script setup lang="ts">
import dayjs from 'dayjs'
import { onMounted, ref, computed } from 'vue'
const num = ref(100)
const time = ref(Date.now())
const numberValue = computed(() => num.value + '')
const timeValue = computed(() => dayjs(time.value).format('HH:mm:ss'))
onMounted(() => {
  setInterval(() => {
    num.value++
    time.value = Date.now()
  }, 1000)
})
</script>

<template>
  <div>
    <NumberScroll :number-string="numberValue" />
    <p>==============</p>
    <NumberScroll :number-string="timeValue" />
    <div>
      <div>默认滚动</div>
      <SeamlessScroll :height="108" style="background-color: #ccc">
        <div style="line-height: 22px">11111111111111111111</div>
        <div style="line-height: 22px">22222222222222222222</div>
        <div style="line-height: 22px">33333333333333333333</div>
        <div style="line-height: 22px">44444444444444444444</div>
        <div style="line-height: 22px">55555555555555555555</div>
        <div style="line-height: 22px">66666666666666666666</div>
      </SeamlessScroll>
    </div>
    <div>
      <div>分步滚动</div>
      <SeamlessScroll
        :height="108"
        :step-height="22"
        :step-wait-timeout="2000"
        style="background-color: #ccc"
      >
        <div style="line-height: 22px">11111111111111111111</div>
        <div style="line-height: 22px">22222222222222222222</div>
        <div style="line-height: 22px">33333333333333333333</div>
        <div style="line-height: 22px">44444444444444444444</div>
        <div style="line-height: 22px">55555555555555555555</div>
        <div style="line-height: 22px">66666666666666666666</div>
      </SeamlessScroll>
    </div>
  </div>
</template>

<style scoped></style>

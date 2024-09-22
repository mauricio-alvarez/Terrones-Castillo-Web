<template>
    <span ref="numberRef">{{ displayNumber }}</span>
  </template>
  
  <script setup>
  import { ref, onMounted, watch } from 'vue'
  import { useIntersectionObserver } from '@vueuse/core'
  
  const props = defineProps({
    value: {
      type: Number,
      required: true
    }
  })
  
  const numberRef = ref(null)
  const displayNumber = ref(0)
  
  const { stop } = useIntersectionObserver(
    numberRef,
    ([{ isIntersecting }]) => {
      if (isIntersecting) {
        animateNumber()
        stop()
      }
    },
    { threshold: 0.1 }
  )
  
  const animateNumber = () => {
    let start = 0
    const end = props.value
    const duration = 2000
    const increment = end / (duration / 16)
  
    const timer = setInterval(() => {
      start += increment
      if (start > end) start = end
      displayNumber.value = Math.floor(start)
      if (start === end) clearInterval(timer)
    }, 16)
  }
  
  watch(() => props.value, (newValue) => {
    displayNumber.value = 0
    animateNumber()
  })
  
  onMounted(() => {
    if (numberRef.value) {
      const observer = new IntersectionObserver(
        ([entry]) => {
          if (entry.isIntersecting) {
            animateNumber()
            observer.disconnect()
          }
        },
        { threshold: 0.1 }
      )
      observer.observe(numberRef.value)
    }
  })
  </script>
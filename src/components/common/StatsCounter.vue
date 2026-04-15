<script>
export default {
  name: "StatsCounter",
  expose: ['reset','startCounter'],
  props: {
    icon: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      count: 0,
      interval: null
    }
  },
  methods: {
    startCounter(target) {
      this.count = 0

      this.interval = setInterval(() => {
        const isFloat = target % 1 !== 0
        if (this.count < target) {
          this.count = parseFloat((this.count + (isFloat ? parseFloat((target / 100).toFixed(2)) : Math.ceil(target / 100))).toFixed(2))
        } else {
          this.count = target
          clearInterval(this.interval)
        }
      }, 20)
    },
    reset() {
      this.count = 0
      clearInterval(this.interval)
    }
  }
  }
</script>

<template>
  <p class=" text-white text-3xl font-bold">
    {{Number(count).toLocaleString()}}{{ icon }}
  </p>
</template>
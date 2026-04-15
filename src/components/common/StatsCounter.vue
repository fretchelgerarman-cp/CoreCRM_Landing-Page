<script>
export default {
  name: "StatsCounter",
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
        if (this.count < target) {
          this.count += Math.ceil(target / 100) 
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
  <h2 class=" text-white">
    {{ count }}
  </h2>
</template>
<script>
import StatsCounter from "../common/StatsCounter.vue"

export default {
  components: {
    StatsCounter
  },
  mounted() {
  
    this.$refs.companies.startCounter(2500)
    this.$refs.contacts.startCounter(1200000)
    this.$refs.satisfaction.startCounter(98)
    this.$refs.integrations.startCounter(50)
  }
}
</script>

<template>
  <div class="text-white text-center stats flex flex-col items-center px-4" style="background: linear-gradient(135deg, var(--emerald-dark), var(--emerald))">
    
    <h3 class="text-3xl font-bold text-white">Simple, transparent pricing</h3>
 <p class="font-thin text-xs text-(--emerald-surface) py-4">Numbers that speaks for themselves.</p>
 
    <div class="grid grid-cols-2 md:grid-cols-4 gap-6 py-10">

      <div>
        <StatsCounter ref="companies" />
        <p>Companies</p>
      </div>

      <div>
        <StatsCounter ref="contacts" />
        <p>Contacts Managed</p>
      </div>

      <div>
        <StatsCounter ref="satisfaction" />
        <p>Satisfaction</p>
      </div>

      <div>
        <StatsCounter ref="integrations" />
        <p>Integrations</p>
      </div>

    </div>
  </div>
</template>
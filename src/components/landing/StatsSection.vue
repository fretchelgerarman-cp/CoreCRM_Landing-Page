<script>
import StatsCounter from "../common/StatsCounter.vue"

export default {
  components: {
    StatsCounter
  },
  mounted() {
  
    this.$refs.companies.startCounter(2500)
    this.$refs.contacts.startCounter(1.2)
    this.$refs.satisfaction.startCounter(98)
    this.$refs.integrations.startCounter(50)
  }
}
</script>

<template>
  <div class="text-white text-center stats flex flex-col items-center px-4" style="background: linear-gradient(135deg, var(--emerald-dark), var(--emerald))">
    
    <h3 class="text-3xl font-bold text-white">Simple, transparent pricing</h3>
 <p class="font-thin text-xs text-(--emerald-surface) py-4">Numbers that speaks for themselves.</p>
 
    <div class="grid grid-cols-2 md:grid-cols-4 gap-6 py-10 text-(--emerald-surface)">

      <div>
        <StatsCounter ref="companies" icon="+" />
        <p class="text-xs">Companies</p>
      </div>

      <div>
        <StatsCounter ref="contacts" icon="M" />
        <p class="text-xs">Contacts Managed</p>
      </div>

      <div>
        <StatsCounter ref="satisfaction" icon="%" />
        <p class="text-xs">Satisfaction</p>
      </div>

      <div>
        <StatsCounter ref="integrations" icon="+" />
        <p class="text-xs ">Integrations</p>
      </div>

    </div>
  </div>
</template>
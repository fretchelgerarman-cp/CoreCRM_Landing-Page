<script>
import PricingCard from '../common/PricingCard.vue'

export default {
    components: { PricingCard },
    data() {
        return {
            isAnnual: false,
            plans: [
                { title: 'Starter', monthlyPrice: 9, annualPrice: 15, description: 'For individuals', features: ['500 contacts', 'Basic pipeline', 'Email integration', 'Mobile app'], popular: false, buttonText: 'Get Started' },
                { title: 'Pro', monthlyPrice: 29, annualPrice: 39, description: 'For growing teams', features: ['5,000 contacts', 'Advanced pipeline', 'Automation workflows', 'Priority support'], popular: true, buttonText: 'Get Started' },
                { title: 'Enterprise', monthlyPrice: 79, annualPrice: 89, description: 'For large orgs', features: ['Unlimited contacts', 'Custom pipelines', 'SSO security', '24/7 support'], popular: false, buttonText: 'Choose Plan' }
            ]
        }
    },
    computed: {
        period() {
            return this.isAnnual ? 'year' : 'mo'
        },
        plansWithPrices() {
            return this.plans.map(plan => ({
                ...plan,
                price: this.isAnnual ? plan.annualPrice : plan.monthlyPrice
            }))
        }
    },
    methods: {
        handlePlanSelect(plan) {
            this.$emit('plan-selected', plan)
        }
    }
}

</script>

<template>
    <div class="pricing flex flex-col items-center gap-4 bg-white">
        <span class="text-xs font-semibold px-4 py-2 rounded-full bg-(--emerald-light) text-(--emerald-dark)">PRICING</span>
        <h3 class="text-3xl font-bold">Simple, transparent pricing</h3>
        <p class="font-thin text-xs text-(--emerald-medium)">No hidden fees. Cancel anytime.</p>
        
        <div class="flex items-center gap-4 mb-8">
            <div class="flex bg-(--emerald-mint) rounded-full p-1">
                <button 
                    @click="isAnnual = false" 
                    class="px-6 py-2 rounded-full text-sm font-medium transition-colors"
                    :class="!isAnnual ? 'bg-(--emerald) text-white' : 'text-(--emerald-dark)'"
                >
                    Monthly
                </button>
                <button 
                    @click="isAnnual = true" 
                    class="px-6 py-2 rounded-full text-sm font-medium transition-colors"
                    :class="isAnnual ? 'bg-(--emerald) text-white' : 'text-(--emerald-dark)'"
                >
                    Annual <span class="text-xs bg-(--emerald-light) text-(--emerald-dark) px-2 py-1 rounded-full">-20%</span>
                </button>
            </div>
        </div>

        <div class="grid grid-cols-1 md:grid-cols-3 gap-6">
            <PricingCard v-for="plan in plansWithPrices" :key="plan.title" :title="plan.title" :price="plan.price" :period="period" :description="plan.description" :features="plan.features" :popular="plan.popular" :button-text="plan.buttonText" @select-plan="handlePlanSelect" />
        </div>
    </div>
</template>
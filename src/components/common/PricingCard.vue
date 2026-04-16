<script>
export default {
    props: ['title', 'price', 'period', 'description', 'features', 'popular', 'buttonText'],
    emits: ['select-plan'],
    methods: {
        handleSelect() {
            this.$emit('select-plan', { title: this.title, price: this.price, period: this.period })
        }
    }
}

</script>

<template>
    <div class="flex flex-col rounded-2xl p-14 border-2 transition-all hover:shadow-lg" :class="popular ? 'bg-(--emerald) border-(--emerald) relative' : 'bg-white border-(--emerald-light)'">
        <div v-if="popular" class="absolute -top-3 left-1/2 transform -translate-x-1/2">
            <span class="bg-(--emerald-dark) text-white text-xs font-semibold rounded-full px-4 py-1 whitespace-nowrap">MOST POPULAR</span>
        </div>
        <div class="flex flex-col justify-center items-center p-4">
          <h3 class="text-xl font-bold mb-2" :class="popular ? 'text-white' : 'text-(--emerald-dark)'">{{ title }}</h3>
          <p class="text-sm mb-6" :class="popular ? 'text-(--emerald-faint)' : 'text-(--emerald-medium)'">{{ description }}</p>
        </div>
        <div class="mb-4 text-center">
            <span class="text-4xl font-bold" :class="popular ? 'text-white' : 'text-(--emerald-dark)'">${{ price }}</span>
            <span :class="popular ? 'text-white' : 'text-(--emerald-medium)'">/{{ period }}</span>
        </div>
      
        <ul class="space-y-3 mb-6 grow">
            <li v-for="(feature, index) in features" :key="index" class="flex items-center gap-2 text-sm" :class="popular ? 'text-(--emerald-faint)' : 'text-(--emerald-dark)'">
                <span :class="popular ? 'text-(--emerald-faint)' : ''">✓</span>
                {{ feature }}
            </li>
        </ul>
        <button 
            @click="handleSelect"
            class="w-full py-3 rounded-xl font-semibold transition-colors"
            :class="popular ? 'bg-white text-(--emerald) hover:bg-emerald-700' : 'bg-(--emerald-surface) text-(--emerald-dark) border border-(--emerald) hover:bg-(--emerald-light)'"
        >
            {{ buttonText }}
        </button>
    </div>
</template>
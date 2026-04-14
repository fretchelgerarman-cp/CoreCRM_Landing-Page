<script>
import { MoveRight } from '@lucide/vue'

export default {
    components: {
        MoveRight
    },
    data() {
        return {
            email: ''
        }
    },
    methods: {
        handleSubmit() {
            console.log(this.email)
        }
    }
}

</script>

<template>
    <div class="bg-(--emerald-mint) flex flex-col gap-4 items-center hero">
        <span class="font-semibold text-xs bg-(--emerald-light) px-4 py-2 rounded-full bg-opacity-5">#1 CRM for Growing Teams</span>
         <h1 class="flex flex-col md:gap-4 items-center text-3xl md:text-5xl">
            <span class="font-bold text-(--emerald-dark)">Manage Contacts.</span>
            <span class="font-bold text-(--emerald-dark)">Close Deals.</span>
            <span class="font-bold text-(--emerald)">Grow Revenue.</span>
        </h1>

        <p class="text-center text-(--emerald-medium)">  Streamline your sales pipeline with smart contact <br> management, 
        real-time analytics, and team <br> collaboration tools.</p>
        <div class="flex gap-2 flex-col sm:flex-row w-full max-w-md"> 
            <input 
            v-model="email" 
            type="text" 
            placeholder="Enter your work email"
             class="bg-white px-4 py-2 h-12 rounded-2xl border border-(--emerald-pale) focus:outline-none focus:ring-2 focus:ring-(--emerald-pale) focus:border-transparent">
            <button @click="handleSubmit" class="px-6 py-2 bg-(--emerald) text-white rounded-2xl hover:bg-(--emerald-dark) transition-colors h-12 flex items-center justify-center gap-2 font-semibold ">
                Start Free 
                <span><MoveRight /></span>
            </button>
        </div>
        <p class="text-center text-xs text-(--emerald-medium)">  Free 14-day trial &nbsp;·&nbsp; No credit card required</p>
        
    </div>
</template>
<script >
import FeatureCard from '../common/FeatureCard.vue'
import { Users, ChartColumn, Mail, BarChart3, Shield } from '@lucide/vue' 
export default {
    components: {
        FeatureCard,
        
    },
    data() {
        return {
            features: [
                {
                    id: 1,
                    icon: Users,
                    title: 'Contact Management',
                    description: 'Organize all your contacts in one place. Tags, notes, and activity history.'
                },
                {
                    id: 2,
                    icon: ChartColumn,
                    title: 'Pipeline Tracking',
                    description: 'Visual drag-and-drop pipeline. See every deal stage at a glance.'
                },
                {
                    id: 3,
                    icon: Mail,
                    title: 'Email Integration',
                    description: 'Sync your inbox. Auto-log emails and track opens and clicks.'
                },
                {
                    id: 4,
                    icon: BarChart3,
                    title: 'Automations',
                    description: 'Set up triggers and workflows. Automate follow-ups and reminders.'
                },
                {
                    id: 5,
                    icon: Users,
                    title: 'Team Collaboration',
                    description: 'Share contacts, assign tasks, and collaborate with your team in real-time.'
                },
                {
                    id: 6,
                    icon: Shield,
                    title: 'Data Security',
                    description: 'Enterprise-grade encryption. GDPR compliant. Your data stays yours.'
                }
            ]
        }
    }
}


</script>

<template>
    <div class="feature flex flex-col items-center gap-4 bg-white py-20">
        <span class="text-xs font-semibold px-4 py-2 rounded-full bg-(--emerald-light) text-(--emerald-dark)">FEATURES</span>
        <h3 class="text-3xl font-bold">Everything you need to close deals</h3>
        <p class="font-thin text-xs text-(--emerald-medium)">Powerful tools, simple interface. Built for teams that move fast.</p>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 max-w-6xl p-10">
            <FeatureCard v-for="feature in features" :key="feature.id" :title="feature.title" :description="feature.description" :icon="feature.icon" />
        </div>

    </div>
</template>
<script >
import FeatureCard from '../common/FeatureCard.vue'
import { AlarmClock } from '@lucide/vue'
export default {
    components: {
        FeatureCard,
        
    },
    data() {
        return {
            features: [
                {
                    id: 1,
                    icon: AlarmClock,
                    title: 'Feature 1',
                    description: 'Description 1'
                },
                {
                    id: 2,
                    icon: AlarmClock,
                    title: 'Feature 2',
                    description: 'Description 2'
                },
                {
                    id: 3,
                    icon: AlarmClock,
                    title: 'Feature 3',
                    description: 'Description 3'
                }
            ]
        }
    }
}


</script>

<template>
    <div>
        <FeatureCard v-for="feature in features" :key="feature.id" :title="feature.title" :description="feature.description" :icon="feature.icon" />

    </div>
</template>
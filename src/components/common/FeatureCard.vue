<script>
export default {
    props: {
        icon: Object,
        title: String,
        description: String
    }
}
</script>


<template>
    <div class="flex flex-col gap-2 bg-(--emerald-surface) border border-(--emerald-light) p-6 rounded-2xl">
        <span    class="bg-(--emerald) p-3 rounded-lg w-fit">
            <component :is="icon" class="text-white" />
        </span>
        <h3 class="font-bold">{{ title }}</h3>
        <p class="text-xs">{{ description }}</p>
    </div>
</template>
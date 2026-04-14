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
    <div>
        <component :is="icon" />
        <h2>{{ title }}</h2>
        <p>{{ description }}</p>
    </div>
</template>
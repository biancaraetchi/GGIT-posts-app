<template>
<div class="card">
        <h3>{{ title }}</h3>
        <span class="mood" :class="mood">mood: {{ mood }}</span>
</div>
</template>
<script>
export default {
    name: "BlogItem",
    props:{
        mood: String,
        title: String
    }
}
</script>
<style>

</style>
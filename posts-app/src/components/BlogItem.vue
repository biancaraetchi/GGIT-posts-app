<template>
<div class="card">
        <h3>{{ title }}</h3>
        <div class="mood" :class="mood">mood: {{ mood }}</div>
        <div>Likes: {{ likes }}</div>
        <div class="likebuttons">
        <button @click="decrementLikes()">Unlike</button>
        <button @click="incrementLikes()">Like</button>
        </div>
</div>
</template>
<script>
export default {
    name: "BlogItem",
    props:{
        mood: String,
        title: String
    },
    data: function(){
        return{
            likes: 0
        }
    },
    methods:{
        incrementLikes: function(){
            this.likes++
        },
        decrementLikes: function(){
            if(this.likes !== 0){
                this.likes--
            }
        }
    }
}
</script>
<style scoped>
.likebuttons{
    display:'flex';
    align-items: 'start';
}
</style>
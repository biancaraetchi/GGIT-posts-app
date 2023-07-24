<template>
<body>
  <div class="smart">
    <h1>My Blog</h1>
    <div class="filter">
    <div>Total likes: {{ likes }}</div>
      <span>filter by:</span>
      <span>mood - <span id="select"></span></span>
    </div>
    <div class="buttons">
      <button @click="mood('')">all</button>
      <button class="sad mood" @click="mood('sad')">sad</button>
      <button class="happy mood" @click="mood('happy')">happy</button>
      <button class="sleepy mood" @click="mood('sleepy')">sleepy</button>
    </div>
    <div class="container" v-for="item in posts" :key="item.id">
      <BlogItem v-if="currentMood === '' || currentMood === item.mood" :mood="item.mood" :title="item.title" :totalLikes="likes" @interface="updateLikes($event)" ></BlogItem>
    </div>
  </div>
  </body>
</template>

<script>
import BlogItem from './BlogItem'
export default {
  name: "BlogList",
  components:{
    BlogItem
  },
  data: function(){
    return{
    likes:0,
    posts:[
        {
            "id":0,
            "mood":"happy",
            "title":"This is how I spent the best day of my life"
        },
        {
            "id":1,
            "mood":"sleepy",
            "title":"Top ten best bedtime stories"
        },
        {
            "id":2,
            "mood":"sad",
            "title":"My program returned a compilation error :(("
        },
        {
            "id":3,
            "mood":"happy",
            "title":"My amazing GGIT experience &lt;33"
        }
    ],
    currentMood:""
      }
  },
  methods:{
    updateLikes: function(event){
      this.likes = event.likes
    },
    mood: function(newMood){
      this.currentMood = newMood
    }
  }
};
</script>

<style>
h1,
.filter,
.buttons {
  text-align: center;
}

.card {
  border: 2px solid black; 

  margin: 15px;
  padding: 0px 0px 10px 10px;
  box-shadow: 0px 0px 7px rgba(0, 0, 0, 0.4);
}

.happy {
  color: lightgreen;
  text-decoration: underline;
}

.sleepy {
  color: blueviolet;
  text-decoration: underline;
  text-decoration-style: wavy;
}

.sad {
  color: blue;
  text-decoration: underline;
  text-decoration-style: dotted;
}

.mood {
  font-weight: 600;
}
</style>

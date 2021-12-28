<template lang="html">
  <section>
    <div v-for="item in array" :key="item.id" class="main">
      <div class="block" :class="item.class">
        <div class="new"><Slider /></div>
        <p>{{ item.text }}</p>
      </div>
    </div>
  </section>
</template>

<script>
import Slider from '@/components/Slider.vue'
import posts from '@/components/posts.js'
export default {
  components:{
    Slider
  },
  data (){
    return{
      array: posts
    }
  }
}
</script>

<style lang="css" scoped>
.main{
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 300px;
}
.block{
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  align-items: center;
  margin-top: 20px;
  background-color: #222222;
  border-radius: 20px;
  width: 80%;
  padding: 20px;
}
p{
  color: white;
  width: 40%;
  margin-top: 20px;
}
.new{
  width: 50%;
  height: 300px;
  margin-top: -40px;
  background-size: cover;
  border-radius: 20px;
}
.one{
  flex-direction: row;
}
.two{
  flex-direction: row-reverse;
}
@media (max-width: 1200px) {
 .block{
   flex-direction: column;
   width: 80%;
   height: 800px;
   font-size: 10px;
 }
 .new{
   width: 90%;
   height: 300px;
   margin-top: 0px;
   background-size: cover;
   border-radius: 20px;
 }
 p{
   color: white;
   width: 90%;
   margin-top: 40px;
 }
}
@media (max-width: 450px) {
 .block{
   flex-direction: column;
   width: 80%;
   height: 800px;
   font-size: 10px;
 }
}
</style>

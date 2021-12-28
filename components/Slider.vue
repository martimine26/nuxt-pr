<template lang="html">
  <div class="main">
    <div class="slider">
      <button type="button" @click="Switch()" id="buttonLeft" style="z-index:1">

      </button>
      <div v-for="item in stas"
      :key="item.id"
      :style="{'background-image': 'url(' + require('@/assets/' + item.photo) + ')', 'display': item.display , 'z-index': 0,}"
      :id="item.id"
      class="slide"
      >
        {{ item.text }}
      </div>
      <button type="button" @click="SwitchTwo()" id="buttonRight" style="z-index:1" ref="bR">

      </button>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return{
      count:0,
      stas:[
        {
          id:3,
          display: 'block',
          photo: 'photo/mihailov.jpg'
        },
        {
          id:2,
          display: 'block',
          photo: 'photo/mihailov.jpg'
        },
        {
          id:1,
          display: 'block',
          photo: 'photo/mirzoevGamid.jpeg'
        },
        {
          id:0,
          display: 'block',
          photo: 'photo/mirzoevAlik.png'
        },
      ]
    }
  },
  mounted(){
    let self = this
    window.addEventListener('load', () => {
      setInterval(function Click(){
        let elemOne = document.getElementById(self.count - 1);
        let elemTwo = document.getElementById(self.count);
        if(elemTwo !== null){
          if(self.count < self.stas.length - 1){
              function animation(elem){
                elem.style.marginLeft = '-800px';
                if(self.count < self.stas.length ){
                  setTimeout(function delay(){
                    elem.style.display = 'none';
                    elem.style.marginLeft = '800px';
                      setTimeout(function del(){
                        elem.style.display = 'block';
                      },50)
                  },500)
                }
              }
            animation(elemTwo)
            self.count += 1;
          }
          else{
          for (let i = 1; i < self.stas.length; i++) {
              let elems = document.getElementById(i - 1);
              elems.style.marginLeft = "0px";
            }
            self.count = 0;
          }
         }
      }, 3000);
    })
  },
  methods:{

  }
}
</script>

<style lang="css" scoped>
.main{
  margin-top: 20px;
  display: flex;
  flex-direction: row;
}
.slider{
  position: relative;
  width: 100%;
	height: 100%;
	margin: auto;
	position: relative;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  overflow: hidden;
  border-radius: 20px;
}
.slide{
  width: 100%;
	height: 100%;
	position: absolute;
	top: 0;
	left: 0;
  transition: 0.55s;
  background-size: cover;
}
.sli1{
  background: green;
}
.sli2{
  background: red;
}
.sli3{
  background: blue;
}
button{
  background: none;
  border: none;
  width: 50px;
  height: 50px;
}
svg{
  color: white;
}
</style>

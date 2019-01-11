
<template>
  <div class='template'>
    <div id='fullpage'>
      <div class="section firstPage">
        <div id="app">
          <div class="logo" v-on:click="axios()"><img src="@/assets/logo.jpeg"></div>
          <router-view/>
          <button class="button" v-on:click="method1()">开始浏览</button>
        </div>
      </div>
      <div class="section secondPage">11111</div>
      <div class="section thridPage">11111</div>
      <div class="section fouthPage">11111</div>
    </div>
  </div>
</template>

<script>

import axios from 'axios'
import { Index } from '../static/js/shouYe.js'
export default {
  name: 'App',
  methods: {
    method1: function () {
      Index();
    },
    axios: function () {
      axios({
        method: 'post',
        data: {
          showapi_appid: '85260', //这里需要改成自己的appid
          showapi_sign: '45d3de268bb041e9b29c86a78332ba78',
        },
      }).then(function(data){
        console.log(data);
      })
    }
  },
  mounted: function () {
    $(document).ready(function(){
      $('#fullpage').fullpage({
        css3: true,
        scrollingSpeed: 1000,
        navigation: true,
        navigationPosition: 'right',
        slidesNavigation: true,
        // slidesNavPosition: "top",
        responsiveHeight: 330,
        dragAndMove: true,
        dragAndMoveKey: 'YWx2YXJvdHJpZ28uY29tX0EyMlpISmhaMEZ1WkUxdmRtVT0wWUc=',
        controlArrows: true,
    });
    })
  }
}
</script>

<style>
.section{
  width: 100%;
  height: 100%;
  background-color: #000;
}
/*firstPage*/
.firstPage{
  background: url('./assets/hangZhou.jpg') no-repeat;
  background-size: cover;
  background-position: center;
  cursor: pointer;
}
.logo>img:hover{
  transform: scale(1.2);
}
.logo{
  width: 120px;
  height: 120px;
  border-radius:60px;
  overflow:hidden;
}
.logo>img{
  width: 120px;
  height: 120px;
  transition: transform 1s;
}
.logo>img{
  width: 100%;
  height: 100%;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  align-items: center;
  flex-direction: column;
  color: #fff;
  height: 300px;
}
.button{
  display: block;
  width: 100px;
  height:40px;
  border-radius:20px;
  background-color:pink;
  color:#fff;
  font-size:16px;
  text-align: center;
  line-height: 40px;
  border:0 solid #fff;
  outline: none;
}
</style>

# 뷰 설치방법
#     1. nodejs 최신버전을 설치 한다
#     2. vscode 설치
#     3. 터미널에서 npm install -g @vue/cli 를 입력 (vue cli설치함)
#     4. vscode extension 설치(Vetur, Html css support, vue 3 Snippets)
#     5. 만약 ERROR 뜨면 yarn을 설치하여 yarn으로 설치한다(안정적이고 빠름)
         (yarn 최신버전을 install 하든지 또는 
#         npm install --global yarn 이렇게도 yarn을 설치 가능하다)
#     6. yarn global add @vue/cli 로 설치함.
# 뷰라우터설치
#     npm install vue-router --save
# project 만들기
#     npm create project명(폴더명)
# 실행방법: npm run serve
#    url 복사후 브라우저에 붙여넣기 하여 띄움
# 강의:https://www.youtube.com/watch?v=-tVaahsXpwk(코딩애플)
# 참조:https://www.youtube.com/watch?v=sqH0u8wN4Rs(한시간만에 끝내는 Vue.js 입문)
#      bootstrap-vue.org 페이지 참조
<template>
<div>
  <div class="black-bg" v-if="modalstat==1">
    <div class="white-bg" >
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
    </div>
    <button @click="modalstat = 0" style="fontsize=20">닫기</button>
  </div>


  <div class="menu">
    <a>Home</a>
    <a>Product</a>
    <a>About</a>
  </div>
  <img alt="Vue logo" src="./assets/logo.png">
  <div>
    <!-- <a v-for="aa in 3" :key="aa"> Home</a> -->
    <!-- <a v-for="aa in 메뉴들" :key="aa"> {{aa}}</a> -->
    <a v-for="(aa,i) in 메뉴들" :key="aa"> {{i}}</a>
  </div>

  <div v-for="(a,i) in rooms" :key="i">
    <img :src="a.image" class="room-img">
    <h4> {{ a.title}}</h4>
    <p> {{ a.price}}원</p>
    <!-- <button @click="f_increase(i)">허위 매물 신고</button> <span>신고수 : {{신고수[i]}}</span> -->
    <!-- <button @click="신고수[i]+=1">허위 매물 신고</button> <span>신고수 : {{신고수[i]}}</span><p></p> -->
  </div>

  <div>
    <!-- <button @click="modalstat = 1">모달창열기</button> -->
    <!-- <button @mouseover="신고수++">허위 매물 신고</button> <span>신고수 : {{신고수}}</span> -->
    <!-- <button @click="신고수++">허위 매물 신고</button> <span>신고수 : {{신고수}}</span> -->
    <!-- <button @click="f_increase">허위 매물 신고</button> <span>신고수 : {{신고수}}</span> -->
  </div>
</div>
</template>

<script>
import oneroom from "./assets/oneroom.js";

export default {
  name:'App',
  data() {
    return{
      modalstat: 0,
      메뉴들:['Home','Shop','About'],
      신고수:[0,0,0],
      price:[50,60,70],
      products:['역삼동원룸','천호동원룸','마포구원룸'],
      rooms : oneroom,
    }
  },
  methods: {
    f_increase() {
      this.신고수[0]++;
    },
  },
  component:{

  }
}  
</script>

<style>

body {
  margin:0;
}

div {
  box-sizing: border-box;
}

.black-bg {
  width:100%;
  height: 200px;
  background: black;
  position:fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 5px;
}
.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color:white;
  padding: 10px;
}
</style>

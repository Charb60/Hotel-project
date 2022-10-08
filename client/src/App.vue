<template>
  <div id="app" class style="font-family: 'Nunito', sans-serif;"> 
    <back-header />
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito&family=Open+Sans&display=swap');

#app {
  font-family: 'Nunito', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 /* text-align: center;*/
  color: #000000; 
  /*margin-top: 10px;*/
}

body {
  position: center;
  background: #fffacd;
  font-family: 'Nunito';
}

/* Fade transition*/
.fade-enter, .fade-leave-to {
  opacity: 0;
}

.fade-enter-active, .fade-leave-active{
  transition: opacity 2.5s;
}

.fade-enter-to {
  opacity: 1;
}

.thumbnail-pic img{
      width: 150px;
    }


  .style{
    font-family: 'Opens Sans';
  }
/* user */
  .bg{
    background: linear-gradient(180deg,  #ceb7b7);
    border-radius: 5px 5px 5px 5px;
    width: 80%;
    height: 100%;
    margin-left: 200px;
    margin-top: 50px;
    padding: 40px;
}

/* Blogs */
 .bg1{
    background: linear-gradient(180deg,  #ceb7b7);
    border-radius: 5px 5px 5px 5px;
    width: 80%;
    height: 100%;
    margin-left: 200px;
    margin-top: 50px;
    padding: 40px;
}

/* Room */
.bg2{
    background: linear-gradient(180deg,  #ceb7b7);
    border-radius: 5px 5px 5px 5px;
    width: 80%;
    height: 100%;
    margin-left: 200px;
    margin-top: 50px;
    padding: 40px;
}

/* Comment */
.bg3{
    background: linear-gradient(180deg,  #ceb7b7);
    border-radius: 5px 5px 5px 5px;
    width: 80%;
    height: 100%;
    margin-left: 200px;
    margin-top: 50px;
    padding: 40px;
}

.bg4{
    background: linear-gradient(180deg, #ceb7b7);
    border-radius: 5px 5px 5px 5px;
    margin-right: 85px;
    width: 70%;
    height: 70%;
}

/* user */
.box{
  width: 100%;
  margin: 0 auto;
  padding: 15px;
  border: 1px;
  /*border-style: dashed;
  border-color: #000000;*/
  background: rgb(245, 245, 245);
  border-radius: 5px 5px 5px 5px; /* ความมนของกรอบ*/
  margin-bottom: 15px; /* ระยะห่างกรอบ */
}
/* user ข้างล่าง*/
.box-1{
  width: 100%;
  margin: 0 auto;
  padding: 15px;
  border: 1px;
  /*border-style: dashed;
  border-color: #000000;*/
  background: white;
  border-radius: 5px 5px 5px 5px; /* ความมนของกรอบ*/
  margin-bottom: 15px; /* ระยะห่างกรอบ */
  color: white; /* สีฟ้อน */
}

/* Blogs */
.box1{
  width: 100%;
  margin: 0 auto;
  padding: 15px;
  border: 1px;
  /*border-style: dashed;
  border-color: #000000;*/
  background: white;
  border-radius: 5px 5px 5px 5px; /* ความมนของกรอบ*/
  margin-bottom: 15px; /* ระยะห่างกรอบ */
}


/* Room */
.box2{
  width: 100%;
  margin: 0 auto;
  padding: 15px;
  border: 1px;
  /*border-style: dashed;
  border-color: #000000;*/
  background: white;
  border-radius: 5px 5px 5px 5px; /* ความมนของกรอบ*/
  margin-bottom: 15px; /* ระยะห่างกรอบ */
}

/* Comment*/
.box3{
  width: 100%;
  margin: 0 auto;
  padding: 15px;
  border: 1px;
  /*border-style: dashed;
  border-color: #000000;*/
  background: white;
  border-radius: 5px 5px 5px 5px; /* ความมนของกรอบ*/
  margin-bottom: 15px; /* ระยะห่างกรอบ */
}

t{
   border-radius: 20px 20px 20px 20px;
    margin: 30px;
}


</style>

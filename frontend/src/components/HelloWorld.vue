<template>
  <nav class="navbar">
    <div class="container-fluid justify-content-center">
      <div id="title" > 玉山歌唱大賽 </div>
    </div>
    <div class="container-fluid justify-content-center">
      <div id="time-middle"><p>{{hour}}:{{minute}} <small id="seconds">{{second}}</small></p></div>
    </div>
  </nav>
  <div >{{msg}}</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    this.hour = new Date().getHours();
    this.minute = new Date().getMinutes();
    this.second = new Date().getSeconds();
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.navbar{
  height:300px;
  background-color: rgb(255, 242, 221);
}
#title{
  text-align: center;
  font-size: 50px;
  // display: flex;
}
#time-middle{
  font-family:'digital-clock-font';
  font-size: 40px;
}
#seconds{
  font-size: 25px;
}
</style>

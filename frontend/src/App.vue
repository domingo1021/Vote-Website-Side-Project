

<template>
  <header>
  <nav class="navbar" id="top-nav">
    <div class="container-fluid justify-content-center">
      <div id="title" > 玉山歌唱大賽 </div>
    </div>
    <div class="container-fluid justify-content-center">
      <div id="time-middle">目前時間: {{Local_time}}</div>
    </div>
    <div class="container-fluid justify-content-center">
     <div id="time-middle">
        <div>倒數計時: {{time_span_object.hours_remaining}}</div>
          <p class="minute-second">時&nbsp;&nbsp;</p>
          <div>{{time_span_object.minutes_remaining}}</div>
          <p class="minute-second">分&nbsp;&nbsp;</p> 
          <div>{{time_span_object.seconds_remaining}}</div>
        <div class="minute-second">秒</div>
      </div>
    </div>
  </nav> 
  </header>
  <body>
    <RouterView :current = "current" :during_event = "during_event"/>
  </body>
</template>


<style scoped>
header + body{
    padding: 20px;
    padding-top: 160px;
}


#top-nav {
  position: fixed;
  background-color: rgb(255, 235, 235);
  border-bottom:1px solid rgb(180, 180, 180);
  height:140px;
  width: 100%;
  font-size: 30px;
  padding-left:20px;
  padding-right:20px;
  text-align: center;
}

#login, #enroll{
  margin-right: 10px;
  border-radius: 5px;
}
#time-middle{
  display: flex;

}

.minute-second{
  font-size: 15px;
  margin-top: 20px;
}
</style>

<script>
export default {
  data() {
    return {
      // 注意 month 0= January, ...
      // current: new Date(),
      current: new Date(2022, 4, 28, 12,59, 55),
      start : new Date(2022,4,28,13 ,0 , 0),
      end: new Date(2022,4 ,28, 13, 0, 5),
      during_event : false
      // end : new Date(2022,4,28,17,0,0),
    }
  },
  computed:{
      time_span_object:{
        get(){
        let time_span = (this.end - this.start)/1000;
        let hours_remaining = Math.floor(time_span/3600);
        let minutes_remaining = Math.floor(time_span/60-hours_remaining*60);
        let seconds_remaning = Math.floor(time_span-hours_remaining*3600-minutes_remaining*60);
        let return_object = {
          "time_span":time_span,
          "hours_remaining":hours_remaining,
          "minutes_remaining":minutes_remaining,
          "seconds_remaining":seconds_remaning,
        }
          return return_object 
        }
      },
      Local_time:{
        get(){
          return this.current.toLocaleString()
        }
      },
      // event_start:{
      //   get(){
      //     // let whether_start = this.current.
      //     // return this.start.getHours
      //   }
      // } 
  },
  methods:{
      countDownTimer () {
      if (this.during_event != true){
          setTimeout(() => {
            this.current = new Date(this.current.getFullYear(),this.current.getMonth(), this.current.getDate(),this.current.getHours(),this.current.getMinutes(),this.current.getSeconds()+1)
            if(this.current.getHours() == this.start.getHours() && this.current.getMinutes()==this.start.getMinutes() && this.current.getSeconds()==this.start.getSeconds()){
              this.during_event = true
            }
            this.countDownTimer()
          }, 1000)
      }else{
          setTimeout(() => {
            this.current = new Date(this.current.getFullYear(),this.current.getMonth(), this.current.getDate(),this.current.getHours(),this.current.getMinutes(),this.current.getSeconds()+1)
            this.start = this.current
            if(this.start.getHours() == this.end.getHours() && this.start.getMinutes()==this.end.getMinutes() && this.start.getSeconds()==this.end.getSeconds()){
              this.during_event = false
            }
            this.countDownTimer()
          }, 1000)
      }
    }
  },
  created() {
    // update the time every second
    this.countDownTimer();
  }
}
</script>

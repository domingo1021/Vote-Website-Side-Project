<template>
  <div class="home">
    <div v-if="!voted">
      <br>
    </div>
    <div v-else>
      你即將投給 --{{target_person}}-- 明日之星
    </div>
    <div v-for="(image,index) in images" :key="index">
      <div class="one-profile">
        <img :src="image.url" :alt="index" :key='index'/>
        <div class="description">
          <div>名字: {{image.description.name}}</div>
          <div>歌名: {{image.description.song_name}}</div>
          <div v-if="!voted">
            <button v-if="during_event" id="vote" @click="clickVote(image.description.name)">投票</button>
            <button v-else id="cant-vote">投票</button>
          </div>
          <div v-else>
            <button v-if="during_event" id="voted" @click="cancelVote()">取消投票</button> 
            <button v-else id="cant-vote">取消投票</button>
            <div>已投票</div>
          </div>

        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
img {
  max-width: 33%;
  height: auto;
}
.one-profile{
  text-align: center;
  font-size: 15px;
  display:block;
  margin-left: auto;
  margin-right: auto;
  background-color: rgb(243, 255, 211);
  margin: 10px;
  width: 30%;
  float:left
}
#vote{
  margin: 5px;
  font-size: 10px;
  border-radius: 5px;
  background-color: rgb(157, 255, 132);
}
#vote:active{
  margin: 5px;
  font-size: 10px;
  border-radius: 5px;
  background-color: rgb(90, 148, 75);
}
#cant-vote{
  margin: 5px;
  font-size: 10px;
  border-radius: 5px;
  background-color: rgb(206, 206, 206);
}
#voted{
  margin: 5px;
  font-size: 10px;
  border-radius: 5px;
  background-color: rgb(255, 100, 100);
}
</style>

<script>
export default {
  name: 'HomeView',
  props:{
    current: Date,
    during_event: Boolean,
  },
  data(){
    return{
        voted: false,
        target_person:"",
        images: [
          { url: require("@/assets/man_1.jpeg"),
            alt: "man1", 
            description:{
              name:"博恩",
              song_name:"哈囉哈囉哈囉"
            }
          },
          { url: require("@/assets/man_2.jpeg"),
            alt: "man2", 
            description:{
              name:"金城武",
              song_name:"哈哈哈哈哈"
            }
          },
          { url: require("@/assets/man_3.jpeg"),
            alt: "man3", 
            description:{
              name:"孔劉",
              song_name:"嘻嘻嘻嘻嘻嘻"
            }
          },
        ]
    }
  },methods:{
    clickVote(person){
      this.voted = true
      this.target_person = person
    },
    cancelVote(){
      this.voted = false
    }
  },
}
</script>

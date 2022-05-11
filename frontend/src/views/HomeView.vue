<template>
  <div class="home">
    <div v-for="(image,index) in images" :key="index">
      <div class="one-profile">
        <img :src="image.url" :alt="index" :key='index'/>
        <div class="description">
          <div>名字: {{image.description.name}}</div>
          <div>歌名: {{image.description.song_name}}</div>
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

</style>

<script>
export default {
  name: 'HomeView',
  data(){
    return{
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
  }
}
</script>

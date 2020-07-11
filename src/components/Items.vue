<template>
  <div class="posts">
    <Item v-for="(post,index) in randomList" :key="index" v-bind:post="post"></Item>
    
  </div>
</template>
<script>
  import Item from './Item.vue';
  export default {
    name: "Items",
    components:{
      Item,
    },
    data: function(){
      return{
        posts: [
          {
            title: "Lorem Ipsum is simply dummy text 1",
            text:"It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
            lists: [
              "Lorem Ipsum has been the industry's",
              "Standard dummy text ever since",
              "But also the leap into electronic typesetting",
            ]
          },
          {
            title: "Lorem Ipsum is simply dummy text 2",
            text:"It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
            lists: [
              "Lorem Ipsum has been the industry's",
              "Standard dummy text ever since",
              "But also the leap into electronic typesetting",
            ]
          },
          {
            title: "Lorem Ipsum is simply dummy text 3",
            text:"It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
            lists: [
              "Lorem Ipsum has been the industry's",
              "Standard dummy text ever since",
              "But also the leap into electronic typesetting",
            ]
          },
          {
            title: "Lorem Ipsum is simply dummy text 4",
            text:"It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout.",
            lists: [
              "Lorem Ipsum has been the industry's",
              "Standard dummy text ever since",
              "But also the leap into electronic typesetting",
            ]
          }
        ],
      }
    },
     computed: {
      randomList: function(){
        return [...this.posts].sort(()=> 0.5 - Math.random());
      }
    }
  }
</script>
<template>
    <div class="post">
        <div class="post__avatar">
          <img src="" class="post__img" alt="">
        </div>
        <div class="post__title">
            {{post.title}}
        </div>
        <div class="post__text">
          {{post.text}}
        </div>
        <ul class="post__list" >
          <li v-for="list in post.lists" :key="list">
            {{list}}
          </li>
        </ul>
    </div>
</template>
<script>
  export default{
    name: "Item",
    props:{
      post:Object,
    }
  }
</script>

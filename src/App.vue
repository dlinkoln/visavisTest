<template>
  <div id="app">
    <section class="contacts__wrapper">
      <div class="container">
        <div class="contacts">
          <h1>
            Lorem Ipsum <br>
            is simply dummy text
          </h1>

          <div class="contacts__form">
            <h2>
              It is a long established
              fact that a reader
            </h2>

            <form id="#contactData" class="ctForm">
              <div class="ctForm__name">
                <label class="ctForm__label" for="name">Name <span class="blue_star">*</span></label><input type="text"
                  name="name">
              </div>
              <div class="ctForm__data">
                <div class="ctForm__phone">
                  <label class="ctForm__label" for="phone">Phone <span class="blue_star">*</span></label><input
                    type="text" name="phone">
                </div>
                <div class="ctForm__email">
                  <label class="ctForm__label" for="email">E-mail <span class="blue_star">*</span></label><input
                    type="text" name="email">
                </div>
              </div>
              <span class="ctForm__notify"><span class="blue_star">*</span> Lorem Ipsum is simply dummy</span>
              <div class="ctForm__range">

              </div>
              <div class="ctForm__send">
                <label for="сtForm__agree"><input type="radio" id="сtForm__agree"> Lorem Ipsum is simply dummy
                  text</label>
                <button class="blue_btn ctForm__btn">
                  Lorem Ipsum
                </button>
              </div>
            </form>
          </div>

        </div>
      </div>
    </section>
    <section class="post__wrapper">
      <div class="container container_posts">
        <Items></Items>
      </div>
    </section>
  </div>
 
</template>

<script>

//  
import Items from './components/Items.vue';

export default {
  name: 'App',
  components: {
    // Item,
    Items,
  }
}
</script>

<style lang="less">
@import url("./less/main.less");
</style>

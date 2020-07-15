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

            <form id="#contactData" class="ctForm" @submit.prevent="checkForm">
              <div class="ctForm__name">
                <label 
                  class="ctForm__label" 
                  for="name"
                >
                  Name 
                  <span class="blue_star">*</span>
                </label>
                <input 
                  class="name" 
                  :class="{notTrsp:name}" 
                  type="text"
                  name="name"  
                  v-model.lazy.trim="name"
                  >
                <span class="ctForm__notify" v-if="this.errors.nameError"><span class="blue_star">*</span> {{this.errors.nameError}}</span>
              </div>
              <div class="ctForm__data">
                <div class="ctForm__phone">
                  <label 
                    class="ctForm__label" 
                    for="phone" 
                    
                  >
                    Phone 
                    <span class="blue_star">*</span>
                  </label>
                  <input
                    type="text"
                    class="phone"
                    :class="{notTrsp:phone}" 
                    v-model.lazy="phone" 
                    name="phone"
                  >
                  <span class="ctForm__notify" v-if="this.errors.phoneError"><span class="blue_star">*</span> {{this.errors.phoneError}}</span>
                </div>
                <div class="ctForm__email">
                  <label 
                    class="ctForm__label" 
                    for="email" 
                    
                  >
                    E-mail 
                    <span class="blue_star">*</span>
                  </label>
                  <input
                    type="text" 
                    class="email" 
                    :class="{notTrsp:email}"  
                    v-model.lazy="email" 
                    name="email"
                    >
                    <span class="ctForm__notify" v-if="this.errors.emailError"><span class="blue_star">*</span> {{this.errors.emailError}}</span>
                </div>
                
              </div>
              
              <div class="ctForm__range">
                <VueRangeSlider 
                
                  max="7000" 
                  step="500" 
                  v-model="value"   
                  piecewise="true"
                  height="4"
                
                  :piecewise-label="true"
                  :label-style="labelStyle"
                >
                </VueRangeSlider>
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
import 'vue-range-component/dist/vue-range-slider.css'
import VueRangeSlider from 'vue-range-component'
export default {
  name: 'App',
  data:function(){
    return{
      name:'',
      phone:'',
      email:'',
      errors:{
        nameError:'',
        phoneError:'',
        emailError:''
      },
    }
  },
  components: {
    Items,
    VueRangeSlider
  },
  methods:{
    checkForm:function(){
      const phoneRegExp = /^\+?([0-9]{2})\)?[-. ]?([0-9]{4})[-. ]?([0-9]{4})$/;
      const emailRegExp = /^\w+@[a-zA-Z_]+?\.[a-zA-Z]{2,3}$/;
      // Name validation
      if(!this.name){
        this.errors.nameError = "Name is required";
      }
      else{
        this.errors.nameError = "";
      }
      // Phone validation
      if(!this.phone){
        this.errors.phoneError = "Phone is required";
      }
      else{
        if(!this.phone.match(phoneRegExp)){
          this.errors.phoneError = "Phone number isnt valid";
        }
        else{
          this.errors.phoneError = "";
        }
      }

      //Email validation
      if(!this.email){
        this.errors.emailError = "Email is required";
      }
      else{
        if(!this.email.match(emailRegExp)){
          this.errors.emailError = "Email isnt valid";
        }
        else{
          this.errors.emailError = "";
        }
      }
      //Msg sending
      if(!this.errors.emailError && !this.errors.passwordError && !this.errors.nameError){
        const url = '/form-sending';
        const data = { name: this.name, email: this.email,phone: this.phone};
        (async function sendData(){
          try {
            const response = await fetch(url, {
              method: 'POST',
              body: JSON.stringify(data), 
              headers: {
                'Content-Type': 'application/json'
              }
            });
            const res = await response;
            alert(`Success: ${res.status}`);
          } catch (error) {
            alert(`Error : ${error}`);
          }
        }())
        return true;
      }
    },
  }
}
</script>

<style lang="less">
@import url("./less/main.less");
.err{
  display:none;
}
.ctForm__name,.ctForm__phone,.ctForm__email{
  &:focus-within{
    label{
      display:none;
    }
  }
}
.dirty{ 
  display:none;
}
.err{
  background:red;
}

.vue-range-slider{
  .slider{
    .piecewise-item{
      height: 4px !important;
      width: 10px !important;
      background: #B4B4B4;
      border-radius: 20px;
      transform: rotate(90deg);
      margin-left:-3px;
      &:nth-child(odd) {
        display:none;
      }
    }
    .piecewise-label{
      &:after{
        content:'грн';
        margin-left:5px;
      }
      transform: rotate(-90deg) !important;
      margin-left: 15px;
      margin-top: -15px;
      width:45px;
      font-family: "Roboto";
      font-style: normal;
      font-weight: normal;
      font-size: 16px !important;
      line-height: 100%;
      text-align: center;
      color: #B4B4B4 !important;
    }
    .slider-dot{
      background-color: #0093E6 !important;
      border-radius: 20px !important;
      border: none;
      box-shadow:none !important;
      width: 10px !important;
      height: 20px !important;
      top: -7px !important;
    }
    .slider-dot.slider-always .slider-tooltip-wrap {
      .slider-tooltip{
        display:flex;
        align-items:center;
        justify-content:center;
        &:before{
          display:none;
          background: #FFFFFF;
        }
        &:after{
          content:'грн';
          margin-left:5px;
          font-family: "Roboto";
        }
        width:100px;
        height:36px;
        border-radius:20px;
        border:2px solid  #0093E6;
        background:#fff;
        font-family: "Roboto";
        font-size: 16px;
        line-height: 100%;
        text-align: center;
        color: #4A4D4E;
      }
    }
  }

}
</style>

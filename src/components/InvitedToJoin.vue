<template lang="html">
    <section class="container">
      <div class="item logo">
        <img src="../assets/image/logo.svg" alt="DagM8 logo">
      </div>
      <div class="item title">
        <h1>{{ title }}</h1>
      </div>
      <div class="item profile">
        <div class="circle">
          <h1>{{ profilePH }}</h1>
        </div>
      </div>
      <div class="item input-email">
        <input type="email" v-model="email" name="email" :placeholder="emailPlaceholder"/>
      </div>
      <div class="item cta">
        <button name="cta" @click="sendConfirmation">{{ ctaTitle }}</button>
      </div>
      <div class="item message" :class="state">
        <div>
          <h1>{{ messageTitle }}</h1>
          <h6>{{ messageSubtitle }}</h6>
        </div>
      </div>
    </section>
</template>

<script>
export default {
  data () {
    return {
      title: 'You been invited to join',
      ctaTitle: 'Continue',
      messageTitle: 'Please enter your edu email.',
      messageSubtitle: '',
      emailPlaceholder: 'What\'s yout edu email?',
      profilePH: 'DM8',
      email: '',
      state: 'empty-email'
    }
  },
  watch: {
    email (newVal, oldVal) {
      if (newVal.length > 0) {
        this.validateEmail()
      } else {
        this.setMessageState(
          'Please enter your edu email.',
          '',
          'empty-email')
      }
    }
  },
  methods: {
    validateEmail () {
      if (this.isEmail(this.email)) {
        this.setMessageState(
          'This email address is valid',
          'please click on continue!',
          'email-success')
      } else {
        this.setMessageState(
          'This email address is not valid...',
          'please try again!',
          'email-error')
      }
    },
    isEmail (text) {
      if (/^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/.test(text)) {
        return true
      } else {
        return false
      }
    },
    sendConfirmation () {
      if (this.isEmail(this.email)) {
        this.setMessageState(
          'Your invitation has been shipped!',
          'Go check your college email inbox',
          'email-success')
      } else {
        this.setMessageState(
          'This email address is not valid...',
          'please try again!',
          'email-error')
      }
    },
    setMessageState (title, subtitle, state) {
      this.messageTitle = title
      this.messageSubtitle = subtitle
      this.state = state
    }
  }
}
</script>

<style lang="css">
  .container{
    display: grid;
    grid-template: repeat(12, 1fr) / 1fr;
    background: white;
    border-radius: 3px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
  }
  .item{
    display: flex;
	  justify-content: center;
	  align-items: center;
  }
  .logo{
    grid-row: 1 / 2;
  }
  .title{
    grid-row: 2 / span 2;
  }
  .profile{
    grid-row: 4 / span 2;
  }
  .input-email{
    grid-row: 6 / span 2;
  }
  .cta{
    grid-row: 8 / span 2;
  }
  .logo img{
    position: absolute;
    width: 20vw;
    transform: translateY(-15%);
  }
  .cta button {
    cursor: pointer;
    background-color: rgba(2, 187, 213, 1.000);
    color: rgba(255,255,255, 0.7);
    border-radius: 5px;
    border: 1px solid rgba(50, 149, 165, 1.000);
    width: 50%;
    height: 50%;
    font-size: 20px;
  }
  .message{
    grid-row: 10 / span 3;
  }
  .email-success{
    background-color: rgba(67, 227, 149, 1.000);
    color: rgba(11, 119, 59, 1.000);
  }
  .email-error{
    background-color: red;
    color: white;
  }
  .empty-email{
    background-color: white;
    color: rgba(190, 190, 190, 1.000);
  }
  .message h1,h6 {
    text-align: center;
    margin: 0;
  }
  input{
    width: 75%;
    height: 40%;
    border-radius: 20px;
    border: 1px solid rgba(204, 204, 204, 1.000);
    color: rgba(204, 204, 204, 1.000);
    padding-left: 10px;
    padding-right: 10px;
    padding-top: 5px;
    padding-bottom: 5px;
    font-size: 20px;
    text-align: center;
  }
  input::placeholder{
    color: rgba(204, 204, 204, 1.000);
    text-align: center;
  }
  .circle{
    display: flex;
	  justify-content: center;
	  align-items: center;
    background-color: rgba(255, 46, 86, 1.000);
    border: 4px solid rgba(155, 19, 58, 1.000);
    border-radius: 50%;
    height: 6vw;
    width: 6vw;
  }
  .circle h1{
    text-align: center;
    font-size: 30px;
    color: white;
  }
  .title h1{
    color: rgba(190, 190, 190, 1.000);
    font-size: 25px;
  }
  @media screen and (max-width: 768px) {
    .logo img{
      transform: translateY(-40%);
    }
    .circle h1{
      font-size: 10px;
    }
  }
</style>

<template>
  <div id="app">
    <section class="component-container">
      <invited-to-join class="content"/>
    </section>
  </div>
</template>

<script>
import InvitedToJoin from './components/InvitedToJoin.vue'

export default {
  name: 'app',
  components: {
    InvitedToJoin
  }
}
</script>

<style lang="css">
  body{
    background-image: url("/background.png");
    background-repeat: repeat;
  }
  #app{
    height: 100vh;
  }
  .component-container{
    display: grid;
    grid-template: 1fr 2fr 1fr / 2fr 3fr 2fr;
    grid-template-areas: ". . ." ". content ." ". . .";
    height: 100vh;
  }
  .content{
    grid-area: content;
  }
  @media screen and (max-width: 768px) {
    .component-container{
      grid-template: 1fr 2fr 1fr / 1fr 3fr 1fr;
    }
  }
</style>

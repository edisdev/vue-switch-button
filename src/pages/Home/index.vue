<script>
import SwitchButton from "@/components/SwitchButton";

export default {
  name: "Home",
  data() {
    return {
      sunshine: false,
      bgColor: '#b5b5b5',
      activeColor: '#009ee0'
    };
  },
  components: {
    SwitchButton
  },
  methods: {
    onChangeValue() {
      this.sunshine = !this.sunshine;
    }
  }
};
</script>

<template>
  <section class="Home">
    <switch-button :switch-value="sunshine"
                   :bg-color="bgColor"
                   :active-bg-color="activeColor" 
                   toggle-content="&#x2639;"
                   toggle-color="#f5f5f5"
                   toggle-active-color="#f5f5f5"
                   toggle-active-content="&#9786;"
                   :toggle-font-color="bgColor"
                   :toggle-active-font-color="activeColor"
                   toggle-font-weight="bold"
                   @input="onChangeValue()"
                   width="180px"
                   height="100px"/>
    <div class="text">
     <span class="active" v-if="sunshine">Yesss ! Thank you Mate &#128512; </span>
     <span v-else>I Am Sorry , Mere Pyaare Jaane Do ...	&#x1F614;</span>
    </div>
  </section>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Open+Sans:400,600,700,800&subset=latin-ext');
  .Home {
    font-family: 'Open Sans', sans-serif;
    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;
    height: 75vh;

    .text {
      margin-top: 20px;
      span {
        font-size: 20px;
        color: #b5b5b5;
        font-weight: bold;
        &.active {
          color: #009ee0;
        }
      }
    }
  }
</style>


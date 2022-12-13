<template>
  <header class="header">
    <div class="lang__switcher" ref="lang_switcher">
      <div class="lang__switcher-toggle" @click="toggleLang">
        👅
      </div>
      <div class="lang__list" ref="lang_list">
        <a href="" class="lang">UK</a>
        <a href="" class="lang">RU</a>
      </div>

    </div>
    <div class="logo">



     <svg width="92" height="51" viewBox="0 0 93 54" fill="none" xmlns="http://www.w3.org/2000/svg">
       <path class="main_path" fill-rule="evenodd" clip-rule="evenodd" d="M0,0H93V54H0Z M41.3354 7.76945L33.3268 9.12369V33.9529L41.3354 35.3073V7.76945ZM29.9096 37.3683V5.70865L44.7524 3.00001V40.0767L29.9096 37.3683ZM73.3736 24.6108V21.1975H81.4311V37.3498H66.1898V5.70721H80.2203V14.1968H76.8047V9.12039H69.6053V33.9366H78.0156V24.6108H73.3736ZM15.7646 31.1724L15.7458 31.088C15.742 31.1049 15.7383 31.1218 15.7346 31.1386L15.7272 31.1724C13.8509 22.6456 11.9808 14.1529 10.12 5.70722H5V37.3496H8.41551V12.6335C8.46538 12.6335 14.1006 37.3656 14.1006 37.3656H17.391C17.391 37.3656 23.0262 12.6335 23.0763 12.6335V37.3496H26.4916V5.70722H21.3715C19.5108 14.1529 17.6408 22.6456 15.7646 31.1724ZM48.5765 9.12045H59.0646L48.5765 33.9365V37.3498H62.7676V33.9365H52.2792L62.7676 9.12045V5.70727H48.5765V9.12045ZM84.8529 37.35H88.2685V5.70741H84.8529V37.35ZM35.1003 48.4751V48.9999H31.8141V44.4293H34.9978V44.9542H32.3907V46.3689H34.4916V46.8936H32.3907V48.4751H35.1003ZM38.3897 44.4292H37.781L39.2414 48.9999H40.3431L41.8039 44.4292H41.208L39.9591 48.4108H39.6386L38.3897 44.4292ZM48.0464 48.4751V48.9999H44.7605V44.4293H47.9442V44.9542H45.3368V46.3689H47.4382V46.8936H45.3368V48.4751H48.0464ZM54.9232 48.9999V44.4292H54.3594V48.251H54.2185L52.092 44.4292H51.1824V48.9999H51.7458V45.1782H51.8871L54.0136 48.9999H54.9232ZM61.4545 44.9417H59.9555V49H59.3786V44.9417H57.8672V44.4293H61.4545V44.9417Z" />

     </svg>


      <span class="svg__fill"></span>


    </div>

  </header>

</template>

<script>
import {gsap} from "gsap";

export default {
  name: "HeaderComponent",
  data() {
    return {
      lang_show: false
    }

  },
  mounted() {

     gsap.fromTo('.svg__fill', {y: 100}, {duration: 3, y: 0});

  },
  methods: {
    toggleLang() {
      if (!this.lang_show) {
        gsap.to(this.$refs.lang_switcher, {duration: 1, width: 170})
        gsap.fromTo(this.$refs.lang_list, {duration: 2, opacity: 0}, {opacity: 1})
        this.lang_show = !this.lang_show
      } else {
        gsap.to(this.$refs.lang_switcher, {duration: 1, width: 38})
        gsap.fromTo(this.$refs.lang_list, {duration: 2, opacity: 1}, {opacity: 0})
        this.lang_show = !this.lang_show
      }


    }
  }
}
</script>

<style lang="scss">
.header {
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;


  .lang__switcher {
    position: absolute;
    left: 0;
    top: 0;
    width: 38px;
    height: 38px;
    border: 1px solid rgba($color: white, $alpha: 0.12);
    border-radius: 38px;
    padding: 9px;
    display: flex;
    align-items: center;
    overflow: hidden;

    &-toggle {
      font-size: 15px;
      cursor: pointer;
    }

    .lang__list {
      margin-left: 20px;

      .lang {
        font-weight: 700;
        margin: 0 10px;
      }
    }
  }

  .logo {
    position: relative;
    -webkit-transform: translateZ(0);
    transform: translateZ(0);
    width: 85px;
    height: 46px;
    background: #BEBEBE;
    overflow: hidden;
    svg {

      z-index: 2;
      position: absolute;
      left: -4px;
      top: -2px;
      right: -2px;

      .main_path {
        fill:#BEBEBE;
        stroke: #000000;
        stroke-width: 1;
      }

    }


    .svg__fill {
      background: black;
      width: 100%;
      height: 100%;
      display: block;
      position: absolute;
      top: 0;
      left: 0;
      z-index: 1;
    }
  }

}


</style>

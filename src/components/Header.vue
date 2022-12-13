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

      <svg class="logo__img" width="85" height="46" viewBox="0 0 85 46" fill="none" xmlns="http://www.w3.org/2000/svg">
        <path class="main_path"
              d="M45.5765 8.12045H56.0646L45.5765 32.9365V36.3499H59.7676V32.9365H49.2792L59.7676 8.12045V4.70728H45.5765V8.12045Z"
              fill="#EFEFEF"/>
        <path class="main_path"
              d="M12.7646 30.1724C12.7583 30.1443 12.7521 30.1161 12.7458 30.088C12.7394 30.1161 12.7335 30.1443 12.7272 30.1724C10.8509 21.6456 8.98077 13.1529 7.11998 4.70722H2V36.3496H5.41551V11.6335C5.46538 11.6335 11.1006 36.3656 11.1006 36.3656H14.391C14.391 36.3656 20.0262 11.6335 20.0763 11.6335V36.3496H23.4916V4.70722H18.3715C16.5108 13.1529 14.6408 21.6456 12.7646 30.1724Z"
              fill="#EFEFEF"/>
        <path class="main_path"
              d="M70.3736 20.1975V23.6108H75.0156V32.9366H66.6053V8.12039H73.8047V13.1968H77.2203V4.70722H63.1898V36.3498H78.4311V20.1975H70.3736Z"
              fill="#EFEFEF"/>
        <path class="main_path" d="M81.8529 36.35H85.2685V4.7074H81.8529V36.35Z" fill="#EFEFEF"/>
        <path class="main_path"
              d="M30.3268 8.12371L38.3353 6.76947V34.3073L30.3268 32.9529V8.12371ZM26.9096 4.70866V36.3683L41.7524 39.0768V2.00002L26.9096 4.70866Z"
              fill="#EFEFEF"/>
        <path class="main_path"
              d="M32.1003 47.4751V47.9999H28.8141V43.4293H31.9978V43.9542H29.3907V45.3689H31.4916V45.8936H29.3907V47.4751H32.1003Z"
              fill="#EFEFEF"/>
        <path class="main_path"
              d="M34.781 43.4292H35.3897L36.6386 47.4108H36.9591L38.208 43.4292H38.8039L37.3431 47.9999H36.2414L34.781 43.4292Z"
              fill="#EFEFEF"/>
        <path class="main_path"
              d="M45.0464 47.4751V47.9999H41.7605V43.4293H44.9442V43.9542H42.3368V45.3689H44.4382V45.8936H42.3368V47.4751H45.0464Z"
              fill="#EFEFEF"/>
        duration
        <path class="main_path"
              d="M51.9232 43.4292V47.9999H51.0136L48.8871 44.1783H48.7458V47.9999H48.1824V43.4292H49.092L51.2185 47.251H51.3594V43.4292H51.9232Z"
              fill="#EFEFEF"/>
        <path class="main_path" d="M58.4545 43.9417H56.9555V48H56.3786V43.9417H54.8672V43.4293H58.4545V43.9417Z"
              fill="#EFEFEF"/>
        <path class="svg_b" d="M0.5 0.5H86.5V49.5H0.5V0.5Z"/>
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

    // gsap.fromTo('.svg__fill', {y: 100}, {duration: 3, y: 0});

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
    margin: 0 auto;
    position: relative;
    -webkit-transform: translateZ(0);
    transform: translateZ(0);
    width: 85px;
    height: 46px;
    background: #BEBEBE;

    .logo__img {

      z-index: 2;
      width: 85px;
      position: absolute;
      left: 0;
      top: 0;

      .main_path {
        fill: transparent;
        stroke: #000000;
        stroke-width: 1;
      }

      .svg_b {
        fill: floralwhite;
      }
    }


    .svg__fill {
      background: green;
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

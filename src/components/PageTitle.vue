<template>
<div class="title__wrapper">
  <h1 class="page__title">
    FULL-CYCLE
    EVENT AGENCY
  </h1>
</div>
</template>

<script>
import {gsap} from "gsap";

export default {
  name: "PageTitle",
  mounted() {
    const offsetDelta = 30;
    gsap.set(".page__title", {xPercent: 0, yPercent: 0});
    let xTo = gsap.quickTo(".page__title", "x", {duration: 0.6, ease: "power3"}),
      yTo = gsap.quickTo(".page__title", "y", {duration: 0.6, ease: "power3"});
    window.addEventListener("mousemove", e => {
      xTo(e.pageX/offsetDelta);
      yTo(e.pageY/offsetDelta);
    });
  }
}
</script>

<style lang="scss">
.title__wrapper{
  z-index: 8;
  .page__title{

    font-weight: 700;
    font-size: 82px;
    line-height: 110%;
    text-align: center;
    text-transform: uppercase;
    color: #373737;
    max-width: 1025px;
  }
}
</style>

<template>
  <div class="marquee__wrapper">
    <div class="marquee revers">
      <span class="clipped__text-reverse">
 FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY
  </span>
      <span class="clipped__text-reverse">
   FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY
  </span>
    </div>
    <div class="marquee">
      <span class="clipped__text">
 FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY
  </span>
      <span class="clipped__text">
   FULL-CYCLE EVENT AGENCY FULL-CYCLE EVENT AGENCY
  </span>
    </div>

  </div>
</template>

<script>
import {gsap, Linear} from "gsap";

export default {
  name: "MarqueeComponent",
  mounted() {

    let marquee = document.querySelectorAll('.clipped__text');
    marquee.forEach(el => {
      let rate = 200;
      let distance = el.clientWidth;
      let style = window.getComputedStyle(el);
      let marginRight = parseInt(style.marginRight) || 0;
      let totalDistance = distance + marginRight;
      let time = totalDistance / rate;
      let container = el.parentElement;
      gsap.to(container, {
        repeat: -1,
        duration: 30,
        x: '-' + totalDistance,
        ease: Linear.easeNone,
      });
    });
    let marqueeReverse = document.querySelectorAll('.clipped__text-reverse');
    marqueeReverse.forEach(el => {
      let rate = 200;
      let distance = el.clientWidth;
      let style = window.getComputedStyle(el);
      let marginRight = parseInt(style.marginRight) || 0;
      let totalDistance = distance + marginRight;
      let time = totalDistance / rate;
      let container = el.parentElement;
      gsap.to(container, {
        repeat: -1,
        duration: 30,
        x: '+' + totalDistance,
        ease: Linear.easeNone,
      });
    });
  }
}
</script>

<style lang="scss">
.marquee__wrapper {
  position: fixed;
  top: 50%;
  left: 0;
  right: 0;
  bottom: 0;
  transform: rotateZ(-28deg);
  white-space: nowrap;
  .marquee.revers{
    transform: rotateZ(-180deg);
  }

  .clipped__text, .clipped__text-reverse {
    display: inline-block;
    font-size: 42px;
    line-height: 110%;
    text-align: center;
    text-transform: uppercase;
    font-weight: 700;
    opacity: 0.1;
    color: transparent;
    -webkit-text-stroke: 1px black;

  }
}
</style>

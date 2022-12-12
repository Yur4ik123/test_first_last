<template>
  <div class="showrell__btn-wrapper">
    <router-link class="showrell__btn" to="/">
      <img class="btn__img" src="@/assets/img/show.svg" width="110" height="109" alt="">

    </router-link>
  </div>

</template>

<script>
import {gsap} from "gsap";

export default {
  name: "ShowrellButton",
  mounted() {
    let rotate = this.rotate();
    document.querySelector('.showrell__btn').addEventListener('mouseover', () => {
      rotate.play();
    })
    document.querySelector('.showrell__btn').addEventListener('mouseout', () => {
      rotate.pause();
    })
  },
  methods: {
    rotate() {
      const tl = gsap.timeline({defaults: {duration: 6, repeat: -1, animationDelay: 0, ease: 'none'}})
      tl.to('.btn__img', {rotation: -360})
      tl.pause();
      return tl;

    }
  }
}
</script>

<style lang="scss">
.showrell__btn-wrapper {
  position: absolute;
  top: 67%;
  right: 40%;
  z-index: 7;

  width: 115px;
  height: 115px;

  .showrell__btn {
    display: block;
    position: relative;

    width: 100%;
    height: 100%;

    img {
      width: inherit;
      height: inherit;
      object-fit: cover;
    }

    &:before {
      position: absolute;
      content: '';
      width: 8px;
      height: 8px;
      top: 50%;
      left: 50%;
      background: black;
      border-radius: 100%;
      transform: translate(-50%, -50%);
    }
  }
}
</style>

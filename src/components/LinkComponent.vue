<template>
  <div class="link__wrapper" ref="link_wrapper">
    <router-link to="/test" v-slot="{ navigate, href }" custom>
      <a :href="href" @click="navigate" class="link" ref="link">{{title}}
        <span class="link__underline " :class="position"></span>
      </a>
    </router-link>
  </div>
</template>

<script>
import {gsap} from "gsap";

export default {
  name: "LinkComponent",
  props: {
    position: {
      default: 'bottom', // left, right
      type: String
    },
    title: {
      default: '',
      type: String
    }
  },
  created() {

  },
  mounted() {
    this.$refs.link_wrapper.classList.add(`${this.position}`)
    this.$refs.link.addEventListener('mouseover', (event) => {
      gsap.to(`.link__underline.${this.position}`, {duration: 0.3, width: '100%'})
    })
    this.$refs.link.addEventListener('mouseout', () => {
      gsap.to(`.link__underline.${this.position}`, {duration: 0.3, width: '0'})
    })
  },
  methods: {}
}
</script>

<style lang="scss">
.link__wrapper {
  position: fixed;
  z-index: 100;

  &.bottom {
    bottom: 19px;
    left: 50%;
    transform: translateX(-50%);

  }

  &.left {
    left: 19px;
    top: 50%;
    transform: translateY(-50%) rotateZ(-90deg);
  }

  &.right {
    right: 19px;
    top: 50%;
    transform: translateY(-50%) rotateZ(90deg);
  }

  .link {
    position: relative;
    display: inline-block;
    font-size: 16px;
    line-height: 140%;
    transition: 0.3s;


    &:hover {
      color: white;
    }

    &__underline {
      position: absolute;
      bottom: 0;
      left: 0;
      background-color: white;
      height: 1px;
      width: 0;
    }
  }
}
</style>

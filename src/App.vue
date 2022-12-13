<template>
  <div id="app">
    <Header class="for_opacity"/>
    <div class="content for_opacity">
      <router-view v-slot="{ Component }">
        <transition>
          <component :is="Component"/>
        </transition>
      </router-view>
    </div>
    <div class="page__transition">
      <h1>
        {{ $route.name }}
      </h1>
    </div>
  </div>
</template>
<script>
import Header from '@/components/Header.vue'
import {gsap} from "gsap";

export default {
  components: {
    Header
  },
  watch: {
    $route(to, from) {
      gsap.set('.page__transition', {right: '100%', left: -100})
      gsap.to('.page__transition', {delay: 1, duration: 1, left: '120%', rotate: 3, ease: "back.out(1.7)"})
      gsap.to('.page__transition', {duration: 2, right: -100, rotate: 3, ease: "back.out(1.7)"})
      gsap.fromTo('.for_opacity', {opacity: 0}, {duration: 1.5, delay: 1, opacity: 1})

    }
  },
}
</script>

<style lang="scss">
body {
  overflow: hidden;
  background: #BEBEBE;
}

#app {
  width: 100vw;
  height: 100vh;
  padding: 19px 19px 19px 24px;

}

.page__transition {
  position: fixed;
  top: -200px;
  right: 100%;
  left: -100;
  bottom: -200px;
  background: blue;
  z-index: 150;
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;

  h1 {
    text-transform: uppercase;
  }
}
.content{
  height: 100%;
}


</style>

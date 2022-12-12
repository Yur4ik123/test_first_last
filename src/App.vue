<template>
  <div id="app">
    <Header/>
    <router-view/>
  </div>
</template>
<script>
import Header from '@/components/Header.vue'

export default {
  components: {
    Header
  }

}
</script>

<style lang="scss">
body {
  overflow: hidden;
}

#app {
  width: 100vw;
  height: 100vh;
  padding: 19px 19px 19px 24px;
  background: #BEBEBE ;
}


</style>

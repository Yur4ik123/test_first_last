<template>
  <div class="home_page">
    <LinkComponent :position="'left'" :title="'where?'"></LinkComponent>
    <LinkComponent :position="'bottom'" :title="'who?'"></LinkComponent>
    <LinkComponent :position="'right'" :title="'what?'"></LinkComponent>
    <ShowreelButton/>
    <div class="background__image">
      <img src="@/assets/img/Ellipse.png" width="578" height="578">
    </div>
    <PageTitle/>
    <MarqueeComponent/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorld,
    LinkComponent: () => import('@/components/LinkComponent.vue'),
    ShowreelButton: () => import('@/components/ShowrellButton.vue'),
    PageTitle: ()=>import('@/components/PageTitle.vue'),
    MarqueeComponent: ()=>import('@/components/MarqueeComponent.vue')
  }
}
</script>
<style lang="scss">
.home_page {
  position: relative;
  height: 100%;
  background-size: 50%;
  display: flex;
  justify-content: center;
  align-items: center;

  .background__image {
    z-index: 5;
    position: absolute;
    left:50%;
    top: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    align-items: center;
    justify-content: center;
    img {
      object-fit: contain;
    }
  }
}

</style>

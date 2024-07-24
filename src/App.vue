<template>
  <CityOverview />
  <Reviews />
  <Chat />
</template>

<script>
import CityOverview from './components/CityOverview.vue'
import Reviews from './components/Reviews.vue'
import Chat from './components/Chat.vue'
export default {
  name: 'App',
  components: {
    CityOverview,
    Reviews,
    Chat
  }
}
</script>

<style lang="scss">
@import "./css/style.scss";
</style>

<template>
  <div id="app">
    <transition name="fade" mode="out-in">
      <router-view></router-view> <!--KOMPONENT ODPOWIEDZIALNY ZA DZIAŁANIE MECHANIZMU TRASOWANIA-->
    </transition>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
#app {

}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s ease-out;

}

.fade-enter, .fade-leave-to {
  opacity: 0;

}
</style>
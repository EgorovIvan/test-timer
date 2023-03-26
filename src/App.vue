<script>
  import Timer from './components/TimerCompoment.vue'
  import AddButton from './components/AddButton.vue'
  
  export default {
    name: 'App',
    components: {
      Timer,
      AddButton
    },
    data() {
      return {
        count: 0,
      }
    },
    methods: {
      addTimer() {
        this.count++
      }
    }
  }
</script>

<template>
  <div class="main">
    <Timer v-for="n in count" :key="n" />
    <AddButton :addTimer="addTimer"/>
  </div>

</template>

<style lang="scss">
  @import "./scss/style.scss";
#app {
  position: relative;
  display: flex;
  margin: 0 auto;
}
</style>

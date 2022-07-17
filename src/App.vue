<template>
  <div class="App">
    <TabForm/>
  </div>
</template>

<script>
import TabForm from './components/Tab-Form.vue'



  export default {
    components: {
    TabForm
},
    data() {
      return {
      }
    },
  }
</script>

<style>

  * {
  box-sizing: border-box;
  padding: 0;
  margin: 10;
}

.App {
  width: 100%;
  height: 100%;
  display: flex;
  overflow: hidden;
}



/* Tab Navigation */
</style>
<!-- <template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  }
}
</script>

 -->

 <template>
  <div id="app">
    <h1>Canvas to PDF Converter</h1>
    <CanvasComponent />
  </div>
</template>

<script>
import CanvasComponent from './components/CanvasComponent.vue';

export default {
  name: 'App',
  components: {
    CanvasComponent,
  },
};
</script>

<style>
#app {
  text-align: center;
  padding: 20px;
}
</style>




<!-- <style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->

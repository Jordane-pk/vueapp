<template>
  <h1>Jordane Ruiz</h1>
    <header>
    <h1>Teds</h1>
    <ul>
      <li>Latest</li>
      <li>Brands</li>
      <li>Collections</li>
      <li class="active">Clearance</li>
    </ul>
  </header>
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

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  justify-content: flex-start;
  align-items: center;
  align-content: normal;

}
h1 {
  color: #deb8bc;
}

header {
  padding: 2em 1em;
  display: grid;
  grid-template-columns: 100px 1fr;
  align-items: center;
}
header h1 {
  font-family: "Allura", serif;
  color: #deb8bc;
}
header ul {
  display: flex;
}
header li {
  margin-right: 3em;
  font-size: 0.85rem;
  font-weight: bold;
}
</style>

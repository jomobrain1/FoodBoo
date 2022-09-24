

<template>
<div>
 
  <Header></Header>
  <section class="container">
    <Meals></Meals>
  </section>

</div>

</template>


<script>
import Header from './components/Header.vue';
import Meals from './components/Meals.vue';
export default{
    components: { Header, Meals },
 
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
 
}
.container{
  max-width: 1200px;
  margin: 0 auto;
  padding: 10px 30px;
}
</style>

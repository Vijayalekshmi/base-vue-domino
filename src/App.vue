<script setup>
import { RouterView } from "vue-router"
</script>
<template>
  <header>
    <AppHeader></AppHeader>
  </header>
  <main class="main">
    <SideBar></SideBar>
    <router-view />
      <!-- <PartsDataTable /> -->
  </main>
  <footer class="footer">
    <AppFooter></AppFooter>
  </footer>
</template>



<script>
import AppHeader from './components/AppHeader.vue';
import AppFooter from './components/AppFooter.vue';


export default {
  name: 'App',
  components: {   
    AppHeader,
    AppFooter
  }
};
</script>

<style>
@import 'primeflex/primeflex.css';

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

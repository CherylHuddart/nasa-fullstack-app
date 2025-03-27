<template>
  <div id="capstone-app">
    <div id="nav">
      <router-link v-bind:to="{ name: 'home' }">Home</router-link>&nbsp;|&nbsp;
      <router-link v-bind:to="{ name: 'collection' }">Collections</router-link>&nbsp;|&nbsp;
      <router-link v-bind:to="{ name: 'neo' }">Near Earth Objects</router-link>&nbsp;|&nbsp;
      <router-link v-bind:to="{ name: 'logout' }" v-if="$store.state.token != ''">Logout</router-link>
    </div>
    <router-view />
  </div>
</template>

<style scoped>
#capstone-app{
  text-align: center;
  font-family: 'Ubuntu', Arial, Helvetica, sans-serif;
}

</style>

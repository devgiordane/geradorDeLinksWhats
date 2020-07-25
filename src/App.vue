<template>
  <div id="app" class="container">
    <keep-alive include="Home">
      <router-view />
    </keep-alive>
  </div>
</template>

<style lang="scss">
@import "./node_modules/bootstrap/scss/bootstrap";
</style>

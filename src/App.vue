<template>
<div id="app">
  <router-view/>
</div>
</template>

<style lang="scss">
@import "~@/assets/style/helper.scss";
@import "~@/assets/style/reset.scss";
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #333;
  font-family: $font-hei;
  font-size: 16px;
  line-height: 1.5;
  background: #f1edea;
  @media(min-width: 478px) {
    &{
      width: 478px;
      margin: 0 auto;
      border: 1px solid #999;
    }
  }
}
</style>

<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>
<style>
    
</style>

<style lang="less">
    @import '~vux/src/styles/1px.less';
    @import './styles/reset.less';
    @import './styles/animate.less';
    #app {
        text-align: center;
        font-size:26px;
        touch-action: none;
    }
</style>

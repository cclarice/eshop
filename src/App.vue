<template>
  <div id="app">
    <Eshop/>
  </div>
</template>

<script>
import Eshop from "@/components/Eshop";

export default {
  name: 'App',
  components: { Eshop }
}
</script>

<!-- Global Application Styles-->
<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Source+Sans+Pro");
@import url("https://fonts.googleapis.com/css?family=Inter");

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html * {
  color: #3F3F3F;
  font-family: "Source Sans Pro", sans-serif !important;
}

html,
body,
#app {
  width: 100vw;
  height: 100%;
  overflow-y: visible;
  overflow-x: hidden;
  &::-webkit-scrollbar {
    position: absolute;
    width: 12px;
    height: 12px;
  }
  &::-webkit-scrollbar-thumb {
    background: #FFFFFF;
    border: 2px solid #ADADAD;
    border-radius: 10px;
  }
  &::-webkit-scrollbar-thumb:hover {
    background: #FFFFFF;
  }
  &::-webkit-scrollbar-track {
    background: #ADADAD;
    border: 4px solid #FAF9F7;
    border-radius: 10px;
  }
}

#app {
  height: auto;
  background-color: #FAF9F7;
}
</style>

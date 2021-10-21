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

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html * {
   color: #000 !important;
   font-family: "Source Sans Pro", sans-serif !important;
}

html,
body,
#app {
  width: 100vw;
  height: 100vh;
}

#app {
  background-color: #FAF9F7;
}
</style>

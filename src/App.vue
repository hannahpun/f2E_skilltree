<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style lang="scss">
body{
  background-color: $bg;
  font-family: 'Roboto';
  color: $w;
  font-size: 16px;
  
}
*{
  box-sizing: border-box;
}
button:focus{
  outline: none;
}

h1{
  font-size: 48px;
  font-style: italic;
  font-weight: bold;
}
h2{
  font-size: 36px;
  font-weight: bold;
}
.remark{
  font-size: 14px;
}
</style>

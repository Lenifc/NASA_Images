<template>
<div class="container">
    <div class="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>

export default {
  name: 'Header',
}
</script>


<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.container{
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
}

a{
  color: white;
  font-size: 1.33rem;
  text-decoration: none;
}
a.router-link-exact-active {
  color: #42b983;
}

.nav{
  padding: 8px 32px;
  background-color: #333;
  width: 100%;

}

</style>

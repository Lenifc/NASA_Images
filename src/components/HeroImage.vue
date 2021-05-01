<template>
    <div class="heroImage"></div>
</template>

<script>
export default {
    name: 'HeroImage'
}
</script>

<style lang="scss">

.heroImage{
    position: fixed;
    z-index: -1;
    height: 100%;
    width: 100%;
    background:
        /* top, transparent black, faked with gradient */ 
        linear-gradient(
          rgba(0, 0, 0, 0.15), 
          rgba(0, 0, 0, 0.15)),
          url('../assets/heroimage.jpg');
    // background-blend-mode: darken;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 80% 0%;
}
</style>
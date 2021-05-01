<template>
    <div class="search">
        <input type="text" placeholder="MOON" name="search" @input="handleChange" :class="{ darkClass: dark }">
      </div>
</template>

<script>
export default {
    name: 'SearchInput',
    props: {
    dark:{
      type: Boolean,
      default: true
    }
  },
    methods:{
        handleChange(e){
            this.$emit('input', e.target.value.trim())
        }
    }
}
</script>

<style lang="scss" scoped>
.search{
  display: flex;
  margin-top: 50px;
}

input{
  padding: 10px;
  border: none;
  border-bottom: 2px solid #ccc;
  margin: 5px;
  color: white;
  background-color: transparent;
  font-size: 1.3rem;
  text-align: center;
}

input::placeholder{
    color: darkgrey;

}

.darkClass{
  color: #1E3D4A;
  border-bottom: 2px solid #1E3D4A; ;
}

</style>
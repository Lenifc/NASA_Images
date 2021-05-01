<template>
  <div class="home">
    <div class="container">
      <transition name="slide">
        <img src="../assets/logo.svg" class="logo" v-if="step === 1">
      </transition>

      <transition name="fade"> 
        <!-- o transition mozna przeczytac w rozbudowanej dokumentacji Vue -->
        <HeroImage v-if="step === 0"/>
      </transition>
      <Claim v-if="step === 0"/>
      <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1"/>
      <div class="result" v-if="results && !loading && step === 1">
        <Item v-for="item in results" :key="item.data[0].nasa_id" :item="item"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import debounce from 'lodash.debounce'
import Claim from '@/components/Claim'
import SearchInput from '@/components/SearchInput'
import HeroImage from "@/components/HeroImage"
import Item from "@/components/Item"
// @ is an alias to /src

const baseURL = 'https://images-api.nasa.gov'

export default {
  name: 'Home',
  data(){
    return{
      searchValue: '',
      results: [],
      loading: false,
      step: 0
    };
  },
  components:{
    Claim,
    SearchInput,
    HeroImage,
    Item
  },
  methods: {
    // debuounce to taki defer - opozni nam dzialanie funkcji o podana ilosc czasu
    handleInput: debounce(function(){
      this.loading = true
      // console.log(this.searchValue)
      //axios pozwala nam na szybkie fetchowanie API
      axios.get(`${baseURL}/search?q=${this.searchValue}&media_type=image`)
      .then(response =>{
        // console.log(response.data.collection.items)
        this.results = response.data.collection.items
        this.loading = false;
        this.step = 1
      })
      .catch(err => console.log(err))
    }, 800),
  },
};
</script>

<style lang="scss" scoped>
.container{
  display: flex;
  position: relative;
  flex-direction: column;
  padding: 20px;
  align-items: center;
  justify-content: center;
  color:white;
  min-height: 100vh;
  height: 100%;
}

// fade na backgroundzie cos nie dziala
.fade-enter-active, .fade-leave-active{
  transition: opacity .5s ease;
}
.fade-enter, .fade-leave-to{
  opacity: 0;
}

.slide-enter-active, .slide-leave-active{
  transition: margin-top .5s ease;
}
.slide-enter, .slide-leave-to{
  margin-top:-50px
}

.logo{
  position: absolute;
  top: 30px;
}

.result{
  display: grid;
  justify-content: center;
  width: 100%;
  grid-template-columns: 1fr 1fr 1fr;
  grid-gap: 20px;
}

</style>
<template>
<div class="app">
  <div class="header container h-100 p-5">
    <h1 class="mb-5">Weather App</h1>
    <div class="d-flex justify-content-center h-100">
      <div class="searchbar w-50 mx-2">
        <input type="text" class="input form-control" v-model="city" placeholder="Enter the city name...">
        
      </div>
      <button class="btn-search btn btn-primary">Search</button>
    </div>
  </div>
  <Weather/>
</div>
</template>
<script>
import Weather from '@/components/Weather.vue'
export default {
  data() {
    return{
      city:'',
      showWeather:false,
    }
  },
  components:{
    Weather
  },
  methods:{
    async searchWeather(){
      this.showWeather=false;
      await this.$nextTick();
      this.showWeather=true;
    }
  }
}
</script>
<style>
body{
  background:#121212 !important;
}
.header{
  background:#212730;
  border-radius:20px;
  color:#f9f9f9;
  text-align:center;
  margin-top:5rem;
}
.btn-search{
  background-image:linear-gradient(to right, cyan,magenta);
}
</style>

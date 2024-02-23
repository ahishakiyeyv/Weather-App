<template>
<div class="container p-0">
    <div class="d-flex">
        <div id="main-div" class="card w-100 mt-3 mb-3">
            <div class="p-3">
                <h2 class="mb-1 day">Today</h2>
                <p class="text-light date mb-1">{{ date }}</p>
                <small class="times">{{ time }}</small>
                <h2 class="place"><img src="../assets/images/loc.svg" alt="location" class="img-loc">{{ name }} <small>{{ country }}</small></h2>
                <div class="temp">
                    <h1 class="weather-temp">{{temperature}} &deg; C</h1>
                    <h2 class="text-gray">{{ description }} <img :scr="iconUrl"/></h2>
                </div>
            </div>
        </div>
        <div class="card card-2 w-100 mt-3 mb-3">
        <table class="m-4">
            <tbody>
                <tr>
                    <th>Sea Level</th>
                    <td v-if="sea_level >0">{{sea_level}}</td>
                    <td v-else>Null</td>
                </tr>
                <tr>
                    <th>Humidity</th>
                    <td>{{humidity}}</td>
                </tr>
                <tr>
                    <th>Wind</th>
                    <td>{{wind}}</td>
                </tr>
            </tbody>
        </table>
        <DaysWeather :cityname="cityname"/>
        <div id="div_Form" class="d-flex m-3 justify-content-center">
            <form action="">
                <input type="button" value="Change Location" @click="changeLocation" class="btn change-btn btn-primary">
            </form>
        </div>
    </div>
    </div>
    
</div>
</template>
<script>
import axios from 'axios'
import DaysWeather from '@/components/DaysWeather.vue'
export default {
  data() {
    return{
        cityname:this.city,
        temperature:null,
        description:null,
        iconUrl:null,
        date:null,
        time:null,
        name:null,
        sea_level:null,
        wind:null,
        country:null,
        humidity:null,
        monthNames:['January','February','March','April','May','June','July','August','September','October','November','December']
    }
  },
  components:{
    DaysWeather
  },
props:{
    city:String
},
methods:{
    changeLocation(){
        window.location.reload()
    }
},
async created(){
    const response = await axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=8331cdef4f10633c84fd856ce65588b0`);
    const weatherData=response.data
    this.temperature=Math.round(weatherData.main.temp);
    this.description=weatherData.weather[0].description;
    this.name=weatherData.name;
    this.wind=weatherData.wind.speed;
    this.sea_level=weatherData.main.sea_level;
    this.country=weatherData.sys.country;
    this.humidity=weatherData.main.humidity;


    this.iconUrl=`https://api.openweathermap.org/img/w/${weatherData.weather[0].icon}.png`;
    const d =new Date();
    this.date=d.getDate() + '-' + this.monthNames[d.getMonth()] + '-' + d.getFullYear();
    this.time=d.getHours() + ':' + d.getMinutes() + ':' + d.getSeconds();
}

}
</script>
<style>
body{
    background:#343d4b;
}
.weather-temp{
    margin:0;
    font-weight:700;
    font-size:4rem;
    padding:2rem 0;
}
h2.mb-1.day{
    font-size:3rem;
    font-weight:400;
}

.img-loc{
    height:70px;
    width:30px;
    color:#fff;
}
#main-div{
    border-radius:20px;
    height:400px;
    color:#fff;
    background-image: url("../assets/images/1.jpg");
    background-size:cover;
    background-position: center;
    background-blend-mode: overlay;
    background-color: rgba(0,0,0,0.5);
    background-repeat: no-repeat;
}
.temp{
    position:absolute;
    bottom:0;
}
.times{
    margin:4rem 0;
}
.main-div:hover{
    transform:scale(1.1);
    transition:transform 0.5s ease;
    z-index:2;
}
.card-2{
    background-color:#212730;
    border-radius: 20px;

}
.card-details{
    margin-left:19px;
}
.h1_left{
    position:absolute;
    bottom:25px;
    left:16px;
    font-size:3vw;
    line-height:1.2;
}
.h3_left{
    position:absolute;
    left:16px;
    font-size:2vw;
    line-height:0.5s;
}
.h3_left small{
    font-size:1rem;
}
table{
    position:relative;
    left:15px;
    border-collapse: separate;
    border-spacing: 15px;
    width:85%;
    text-align:left;
    max-width:600px;
    margin:0 auto;
}
th,td{
    font-size:18px;
    color:#f9f9f9;

}
td{
    text-align:left;
}
table,tr:hover{
    color:red;
}
.change-btn{
    background-image: linear-gradient(to right,cyan, magenta);
}
.change-btn:hover{
    transform: scale(0.9);
    transition:transform 0.1s ease;
}

</style>

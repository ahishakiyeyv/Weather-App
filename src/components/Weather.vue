<template>
<div class="container p-0">
    <div class="d-flex">
        <div class="card main-div w-100 mt-3">
            <div class="p-3">
                <h2 class="mb-1 day">Tuesday</h2>
                <p class="text-light date mb-0">Date</p>
                <small>time</small>
                <h2 class="place">location icone <small>country</small></h2>
                <div class="temp">
                    <h1 class="weather-temp">19deg</h1>
                    <h2 class="text-light">description</h2>
                </div>
            </div>
        </div>
        <div class="card card-2 w-100 mt-3">
        <table class="m-4">
            <tbody>
                <tr>
                    <th>Sea Level</th>
                    <td>100</td>
                </tr>
                <tr>
                    <th>Sea Level</th>
                    <td>100</td>
                </tr>
                <tr>
                    <th>Sea Level</th>
                    <td>100</td>
                </tr>
            </tbody>
        </table>
        <DaysWeather/>
        <div id="div_Form" class="d-flex m-3 justify-content-center">
            <form action="">
                <input type="button" value="Change Location" class="btn change-btn btn-primary">
            </form>
        </div>
    </div>
    </div>
    
</div>
</template>
<script>
import DaysWeather from '@/components/DaysWeather.vue'
export default {
  data() {
    return{

    }
  },
  components:{
    DaysWeather
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
}
h2.mb-1.day{
    font-size:3rem;
    font-weight:400;
}
.main-div{
    border-radius:20px;
    color:#fff;
    background-image:url(https://www.google.com/url?sa=i&url=https%3A%2F%2Fwww.wired.com%2Fstory%2Fthis-heat-is-shaking-the-very-foundation-of-the-ocean-food-web%2F&psig=AOvVaw2ZZiA7kT16rO0NmEvzIPI8&ust=1708731524499000&source=images&cd=vfe&opi=89978449&ved=0CBIQjRxqFwoTCNCpvJOPwIQDFQAAAAAdAAAAABAE);
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
.main-div:hover{
    transform:scale(1.1);
    transition:transform 0.5s ease;
    z-index:2;
}
.card2{
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
    color:#fff;

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

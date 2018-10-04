<template>
  <div class="hava">

      <h3> {{weather.name}}, {{weather.sys.country}} </h3>
      <h4>{{ weather.main.temp.toPrecision(3) }}  °C</h4>
      <h5 class="desc"> {{weather.weather[0].description}}</h5>

      <img class="img" v-bind:src="b"/>
  </div>
</template>

<script>
import axios from 'axios'

  export default {

    data() {
        return {
        weather: []
      }
    },
    computed: {

    b: function () {

       return "http://openweathermap.org/img/w/"+ this.weather.weather[0].icon + ".png";
    }
  },

   created: function()
        {
            this.fetchItems();
        },

     methods: {
       fetchItems()
            {
        axios.get('http://api.openweathermap.org/data/2.5/weather?q=Istanbul&units=metric&APPID=Your Open Weather Key')
        .then((response) => {
          this.weather = response.data;
          console.log(response);
        });
      }
      }
};

</script>

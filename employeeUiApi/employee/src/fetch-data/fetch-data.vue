<template>
  <div>
    <h1>Weather forecast</h1>
    <p>This component demonstrates fetching data from the server.</p>
    <p v-if="!forecasts">
      <em>Loading...</em>
    </p>
    <table class="table" v-if="forecasts">
      <thead>
        <tr>
          <th>Date</th>
          <th>Temp. (C)</th>
          <th>Temp. (F)</th>
          <th>Summary</th>
        </tr>
      </thead>
      <tbody>
        <tr v-bind:key="index" v-for="(forecast, index) in forecasts">
          <td>{{ forecast.dateFormatted }}</td>
          <td>{{ forecast.temperatureC }}</td>
          <td>{{ forecast.temperatureF }}</td>
          <td>{{ forecast.summary }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
/* eslint-disable */
import { FetchDataService } from "../service/fetchdata.service";

export default {
  name: "FetchData",

  data() {
    return {
      forecasts: []
    };
  },

  mounted() {
    console.log("in Mounted");
    this.getWeatherForecasts();
  },

  methods: {
    getWeatherForecasts() {
      console.log("in get");

      FetchDataService.getWeatherForecasts()
        .then(res => {
          this.forecasts = res;
          console.dirxml(res);
        })
        .catch(error => {
          console.log("There is an error in Get API call.", error);
        });
    }
  }
};
</script>
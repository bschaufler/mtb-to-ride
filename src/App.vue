<template>
  <div id='app'>
    <h1 class="ui dividing centered header">Mountain Bike To-Ride list</h1>
    <div class='ui grid'>
      <div class="column">
        <bike-ride-list v-bind:bikeRides="bikeRides"></bike-ride-list>
        <create-bike-ride v-on:create-bike-ride="CreateBikeRide"></create-bike-ride>
      </div>
    </div>
  </div>
</template>

<script>
import BikeRideList from './components/BikeRideList';
import CreateBikeRide from './components/CreateBikeRide';

export default {
  name: 'app',
  components: {
    BikeRideList,
    CreateBikeRide,
  },
  data() {
    return {
      bikeRides: [{
        id: 1,
        title: 'Buffalo Creek',
        rating: 'Moderate',
        done: false,
      }, {
        id: 2,
        title: 'Centenial Cone',
        rating: 'Moderate',
        done: true,
      }, {
        id: 3,
        title: 'Porcupine Rim',
        rating: 'Hard',
        done: false,
      }, {
        id: 4,
        title: 'Slim Shady Trail',
        rating: 'Moderate',
        done: false,
      },
      {
        id: 5,
        title: 'Green Mountain',
        rating: 'Easy',
        done: false,
      }],
    
    };
  },
  methods: {
    CreateBikeRide(newRide) {
      this.bikeRides.push(newRide);
    },
  },
};
</script>

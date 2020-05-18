<template>
  <div>
    <p class="tasks">Completed Rides: {{bikeRides.filter(ride => {return ride.done === true}).length}}</p>
    <p class="tasks">Pending Rides: {{bikeRides.filter(ride => {return ride.done === false}).length}}</p>
  <div class="ui four column grid">
    <bike-ride v-on:delete-ride="deleteRide" v-on:complete-ride="completeBikeRide" v-for="ride in bikeRides" :key="ride.id" :ride.sync="ride"></bike-ride>
    </div>
  </div>
</template>

<script type = "text/javascript" >
import BikeRide from './BikeRide';

export default {
  props: ['bikeRides'],
  components: {
    BikeRide,
  },
  methods: {
    deleteRide(ride) {
        this.bikeRides.splice(this.bikeRides.indexOf(ride), 1);
    },
    completeBikeRide(ride) {
      this.bikeRides[this.bikeRides.indexOf(ride)].done = true;
    },
  },
};
</script>

<style scoped>
p.tasks {
  text-align: center;
}
</style>


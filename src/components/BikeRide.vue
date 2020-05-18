<template>
<div class="column">
  <div class='ui centered card'>
    <div class="content" v-show="!isEditing">
      <div class='header'>
          {{ ride.title }}
      </div>
      <div class='meta'>
          {{ ride.rating }}
      </div>
      <div class='extra content'>
          <span class='right floated edit icon' v-on:click="showForm">
          <i class='edit icon'></i>
        </span>
        <span class='right floated trash icon' v-on:click="deleteRide(ride)">
          <i class='trash icon'></i>
        </span>
      </div>
    </div>
    <div class="content" v-show="isEditing">
      <div class='ui form'>
        <div class='field'>
          <label>Title</label>
          <input type='text' v-model="ride.title" >
        </div>
        <div class='field'>
          <label>Skill Level</label>
          <input type='text' v-model="ride.rating" >
        </div>
        <div class='ui two button attached buttons'>
          <button class='ui basic blue button' v-on:click="hideForm">
            Close X
          </button>
        </div>
      </div>
    </div>
    <div class='ui bottom attached green basic button' v-show="!isEditing &&ride.done" disabled>
        Completed
    </div>
    <div class='ui bottom attached red basic button' v-on:click="completeRide(ride)" v-show="!isEditing && !ride.done">
        Awaiting to Be Ridden
    </div>
  </div>
  </div>
</template>

<script type="text/javascript">
  export default {
    props: ['ride'],
    data() {
      return {
        isEditing: false,
      };
    },
    methods: {
      completeRide(ride) {
        this.$emit('complete-ride', ride);
      },
      deleteRide(ride) {
        this.$emit('delete-ride', ride);
      },
      showForm() {
        this.isEditing = true;
      },
      hideForm() {
        this.isEditing = false;
      },
    },
  };
</script>

<template>
  <div class="row">
    <div class="col-lg-12">
      <div class="card text-center">
        <div class="card-header text-white bg-dark">
          <ul class="nav nav-pills card-header-pills">
          <li class="nav-item">
            <router-link class="nav-link active" to="/Routines">Routines</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/Addroutines">Add a Routine</router-link>
          </li>
          <li class="nav-item">
            <router-link class="nav-link" to="/Myroutines">My Routines</router-link>
          </li>
        </ul>
        <div>
            <h1> Routine List:</h1>
            <table class="table table-light">
              <thead>
                <tr>
                  <th scope="col">Routine Name</th>
                  <th scope="col">Routine Description</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="routine in routines" :key="routine.id">
                  <th scope="row">{{routine.routineName}}</th>
                  <td>{{routine.routineDescription}}</td>
                  <td><button @click="view(routine.routine_id)" class="btn btn-primary">View</button></td>
                </tr>
              </tbody>
            </table>
        </div>
        </div>
    </div>
  </div>
</div>
</template>

<script>
import { Globals } from '@/models/api';
import { GetRoutines } from '@/models/routines';

export default {
  data: () => ({
    Globals: Globals,
    routines: [],
  }),
  async mounted() {
    this.routines = await GetRoutines();
  },
  methods: {
    async view(data) {
      Globals.routine = data;
      this.$router.push('/viewroutines');
    },
  },
};
</script>

<style>

</style>

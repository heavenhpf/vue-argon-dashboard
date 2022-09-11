<template>
  <div class="card" id="top">
    <div class="card-header pb-0">
      <h3>Get User</h3>
    </div>
    <div class="card-body px-0 pt-0 pb-2">
      <div class="table-responsive p-4">
        <table class="table align-items-center text-center">
          <thead>
            <tr>
              <th class="text-uppercase font-weight-bolder opacity-7">Avatar</th>
              <th class="text-uppercase font-weight-bolder opacity-7">Name</th>
              <th class="text-uppercase font-weight-bolder opacity-7">Email</th>
            </tr>
          </thead>
          <tbody v-if="get && get.length">
            <tr v-for="get of get">
              <td>
                <img :src=get.avatar class="avatar avatar-xl" />
              </td>
              <td>
                <h5 class="font-weight-bold mb-0">{{get.first_name}} {{get.last_name}}</h5>
              </td>
              <td>
                <h5 class="font-weight-bold mb-0">{{get.email}}</h5>
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "authors-table",
  data() {
    return {
      get: []
    }
  },
  created() {
    axios.get('https://reqres.in/api/users')
      .then(response => {
        this.get = response.data.data
      })
  }
}
</script> 
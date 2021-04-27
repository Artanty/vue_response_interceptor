<template>
  <div>
    <ul>
      <li v-for="(item,index) in items" :key="index">
      {{ item.type }} : {{ item.value }}
      </li>
    </ul>
  </div>
</template>

<script lang="ts">

import axios from "axios";

export default {
  data () {
      return{
        items: []
      }
  },
  mounted() {
    this.apiRequest('https://run.mocky.io/v3/bb0f15d5-d5b5-4a4e-b8b2-d9dc4281e894')
    this.apiRequest('https://run.mocky.io/v3/3808fd63-51e8-444e-9698-c35879f544c6')
  },
  methods: {
    apiRequest(url){
      axios.interceptors.response.use((response) => {
        if (response.data.errorCode > 0) {
          return Promise.reject(response.data.errorMessage)
        }
        return response
      })
      axios.get(url)
      .then(response => this.items.push({type: 'response', value: response.data.data}))
      .catch(error => this.items.push({type: 'error', value: error}))
    }
  }
}
</script>
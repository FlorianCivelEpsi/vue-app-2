<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/parking.jpeg" height="250px" width="300px;">
    <Search msg="TrouveTonParking.com"/>
  </div>
</template>

<script>
// @ is an alias to /src
import Search from '@/components/Search.vue'

export default {
  name: 'Home',
  components: {
    Search
  }
}
</script>

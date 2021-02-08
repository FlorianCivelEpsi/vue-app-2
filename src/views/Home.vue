<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/parking.jpeg" height="250px" width="300px;">
    <Search msg="TrouveTonParking.com"/>
    <br>
    <input v-model = "parkin" placeholder="Nom parking">
    <br>
    {{parkin}}
    <br>
    <input v-on:click="research()" type="submit" value="Rechercher">
    <br>
    <pre> {{info}}</pre>
  </div>
</template>


<script src="https://unpkg.com/axios/dist/axios.min.js"></script>
<script>
// @ is an alias to /src
import Search from '@/components/Search.vue'

export default {
  name: 'Home',
    props: {
	parkin: null,
  info: null
  },
  mounted () {
          axios
            .get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parkings-publics-nantes&q=' + 'Parking%20Cit%C3%A9%20des%20Congr%C3%A8s')
            .then(response => (this.info = response.data))
            .catch(error => console.log(error))
        },
  components: {
    Search
  },
   /*
  methods: {
    research: function(){
					 axios
            .get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parkings-publics-nantes&q=' + 'Parking%20Cit%C3%A9%20des%20Congr%C3%A8s')
            .then(response => (this.info = response.data))
            .catch(error => console.log(error))
    }, 
    } */

}
</script>

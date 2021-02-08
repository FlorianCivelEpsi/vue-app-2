<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/parking.jpeg" height="250px" width="300px;">
   
    <p>
      Veuillez rechercher votre position ou parking spécifique : 
    </p>
    <br>
    <input v-model = "parkin" placeholder="Nom parking">
    <br>
    {{parkin}}
    <br>
    <input v-on:click="research()" type="submit" value="Rechercher">
    <br>
    <pre>{{info}}</pre>
    <pre></pre>
    <!--<pre>{{info.records[0].fields.telephone}}</pre> -->
    <br>
     <Search msg="Résultat : "/>
  </div>
</template>


<script>
// @ is an alias to /src
import Search from '@/components/Search.vue'
import axios from 'axios';

export default {
  name: 'Home',
    props: {
  info: null,
  test: null,
  url: 'https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parkings-publics-nantes&q=',
  namePark: 'Parking%20Cit%C3%A9%20des%20Congr%C3%A8s',
  },
 
  components: {
    Search
  },
        
   
  methods: {
    research(){
					 axios
            .get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parkings-publics-nantes&q=Parking%20Cit%C3%A9%20des%20Congr%C3%A8s')
            .then(response => (this.info = response.data))
            .catch(error => console.log(error))
            return info, test;
    }, 
    } 

}
</script>

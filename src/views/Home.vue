<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/parking.jpeg" height="250px" width="300px;">
   
    <p>
      Veuillez rechercher votre position ou parking spécifique : (Parking Cité des Congrès)
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
     <Search :info="infos" msg="Résultat : "/>
  </div>
</template>


<script>
// @ is an alias to /src
import Search from '@/components/Search.vue'
import axios from 'axios';

export default {
  name: 'Home',
    props: {

  },
  data(){
    return{
nameP: 'Parking Cité des Congrès',
parkin: null,
info : null,
    }
    
  },
 
  components: {
    Search
  },
        
   
  methods: {
    research(){
           let nomParking = this.parkin;
					 axios
            .get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parkings-publics-nantes',{
              params:{
                q: nomParking,
              }
            })
            .then(response => (this.info = response.data))
            .catch(error => console.log(error))
            return info, test;
    }, 
    } 

}
</script>

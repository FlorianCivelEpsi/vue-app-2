<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/parking.jpeg" height="250px" width="300px;">
   
    <p>
      Veuillez rechercher un parking : (Parking Cité des Congrès, Parking Gare Château, Parking Tour Bretagne)
    </p>
    <br>
    <input v-model = "parkin" placeholder="Nom parking">
    <br>
    {{parkin}}
    <br>
    <br>
    <input v-on:click="research()" type="submit" value="Rechercher">
   <br>
  
    <!--<pre>{{info.records[0].fields.telephone}}</pre> -->
    <br>
    <li v-if="afficheSearch == 'ok'">
     <Search :info="info" msg="Résultat : "/> 
        <input v-on:click="localise()" type="submit" value="Situer">
    </li>
     <li v-if="situer == 'ok'">
     <HereMap  :center="center" />
     </li>
  </div>
</template>


<script>
// @ is an alias to /src
import Search from '@/components/Search.vue'
import axios from 'axios';
import HereMap from '@/components/HereMap.vue'


export default {
  name: 'Home',
   
  data(){
    return{
parkin: null,
info : null,
afficheSearch: null,
situer: null,
center:{ 
    lat: null, 
    lng: null
    }
    }
  },
 
  components: {
    Search,
    HereMap,
  },
  methods: {
    research(){
           let nomParking = this.parkin;
           let a1;
           let a2;
					 axios
            .get('https://data.nantesmetropole.fr/api/records/1.0/search/?dataset=244400404_parkings-publics-nantes',{
              params:{
                q: nomParking,
              }
            })
            .then(response => (this.info = response.data))
            .catch(error => console.log(error))
            this.afficheSearch = 'ok';
            return info;
    }, 
    localise(){
            this.center.lat = this.info.records[0].fields.location[0];
            this.center.lng = this.info.records[0].fields.location[1];
            this.situer = 'ok';
    }
    } 

}
</script>

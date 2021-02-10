<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/parking.jpeg" height="250px" width="300px;">
   
    <p>
      Veuillez rechercher un parking : (ex : Parking Cité des Congrès, Parking Gare Château, Parking Tour Bretagne, etc...)
    </p>
    <br>
    <input v-model = "parkin" placeholder="Nom parking">
    <br>
    {{parkin}}
    <br>
    <br>
    <input v-on:click="research()" type="submit" value="Rechercher">
   <br>
   <br>
      <div id="inf">
    <!--<pre>{{info.records[0].fields.telephone}}</pre> -->
    <li id="sit" v-if="afficheSearch == 'ok'">
     <Search :info="info" msg="Résultat : "/> 
        <input v-on:click="localise()" type="submit" value="Situer">
    </li>
    </div>
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
<style scoped>
#inf{
  background-color:  #358fda;
  color: aliceblue;

}
#sit{
  padding-bottom: 20px;

}
input[type=button], input[type=submit], input[type=reset] {
  background-color: #10597a;
  border: none;
  color: white;
  padding: 16px 32px;
  text-decoration: none;
  margin: 4px 2px;
  cursor: pointer;
    border-radius: 10px;
}
  
</style>
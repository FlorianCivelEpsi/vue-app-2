<template>
  <div id="app">
	      <h1>Réusltat : </h1>
        <br>
    <!-- 
	  <nav v-bind:class="active" v-on:click.prevent>
		<a href="" v-on:click="toggleActive('parkVelo')">Parking vélo</a>
		<a href="#"  v-on:click="makeActive('parkMoto')">Parking moto</a>
		<a href=""  v-on:click="makeActive('pmr')">Accès PMR</a>
		<a href="#"  v-on:click="makeActive('paiement')">Moyen paiement</a>
      </nav>   
	-->
	<br>
	<p>Nom : {{info.parameters.q}} </p>
	<br>
    <p>Téléphone : {{info.records[0].fields.telephone}} </p>
	<br>
	<p>Présentation : {{info.records[0].fields.presentation}} </p>
	<br>
	<p>Accès transport en commun : {{info.records[0].fields.acces_transports_communs}} </p>
	<br>
    <p>Localisation : {{info.records[0].fields.location}} </p>
	<br>
	
	
    <!--
    <li v-for="service in services" v-on:click="toggleActive(service)" v-bind:key="{ 'active': service.active}">

			Display the name and price for every entry in the array .
                 Vue.js has a built in currency filter for formatting the price 

			{{service.name}}  

	</li>
    -->
  </div>
</template>

<script>
/* import axios from 'axios'; */

export default {
  
 name: 'Search',
props:["info"],
  
  methods: {
	
  },
	 
     

} 
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
 <style scoped>

	*{
		margin:0;
		padding:0;
	}

	body{
		font:15px/1.3 'Open Sans', sans-serif;
		color: #5e5b64;
		text-align:center;
	}

	a, a:visited {
		outline:none;
		color:#389dc1;
	}

	a:hover{
		text-decoration:none;
	}

	section, footer, header, aside, nav{
		display: block;
	}

	/*-------------------------
		The menu
	--------------------------*/

	nav{
		display:inline-block;
		margin:60px auto 45px;
		background-color:#5597b4;
		box-shadow:0 1px 1px #ccc;
		border-radius:2px;
	}

	nav a{
		display:inline-block;
		padding: 18px 30px;
		color:#fff !important;
		font-weight:bold;
		font-size:16px;
		text-decoration:none !important;
		line-height:1;
		text-transform: uppercase;
		background-color:transparent;

		-webkit-transition:background-color 0.25s;
		-moz-transition:background-color 0.25s;
		transition:background-color 0.25s;
	}

	nav a:first-child{
		border-radius:2px 0 0 2px;
	}

	nav a:last-child{
		border-radius:0 2px 2px 0;
	}

	nav.home .home,
	nav.projects .projects,
	nav.services .services,
	nav.contact .contact{
		background-color:#e35885;
	}

	p{
		/*font-size:22px;
		font-weight:bold;
		color:#7d9098; */
	}

	p b{
		color:#ffffff;
		display:inline-block;
		padding:5px 10px;
		background-color:#c4d7e0;
		border-radius:2px;
		text-transform:uppercase;
		font-size:18px;
	}

    </style>
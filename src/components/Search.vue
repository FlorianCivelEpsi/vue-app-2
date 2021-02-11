<template>
  <div id="app">
<br>
	      <h1>Réusltat : </h1>
        
  
	
	<p>Nom : {{info.parameters.q}} </p>
	
    <p>Téléphone : {{info.records[0].fields.telephone}} </p>
	
	<p>Présentation : {{info.records[0].fields.presentation}} </p>
	
	<p>Accès transport en commun : {{info.records[0].fields.acces_transports_communs}} </p>
	    <p id="bot">Localisation : {{info.records[0].fields.location}} </p>
	

  </div>
</template>

<script>
export default {
  
 name: 'Search',
props:["info"],
  
  methods: {
	
  },
	 
     

} 
</script>

 <style scoped>


	body{
		font:15px/1.3 'Open Sans', sans-serif;
		color: white;
		text-align:center;

	}

	p b{
		color:#ffffff;
		display:inline-block;
		
		border-radius:2px;
		text-transform:uppercase;
		font-size:18px;
	}
	
    </style>
<template>

  <div id="app">
    <div id="nav">

      
 <a><router-link to="/">Home</router-link> </a>  |  
<a> <router-link to="/about">About</router-link></a>
	<div class="animation start-home"></div>


    
    </div>
    <router-view/>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
a{
 font-weight: bold;
 color: black;
}


</style>

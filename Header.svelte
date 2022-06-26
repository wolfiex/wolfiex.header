<script>
import { onMount } from 'svelte';

// import './css/header.css'

const host = 'danielellisresearch.com'
const menu = [
    // {href:'#', name:''},
    {href:'https://showcase.'+host, name:'Showcase'},
    {href:'https://medium.'+host, name:'Published_Articles'},
    {href:'https://research.'+host, name:'PhD'},
    {href:'https://coaching.'+host, name:'Adventure_Coaching'},
    {href:'https://art.'+host, name:'Art'},

    {href:'#contact', name:' Hire',active:true},// cv
] ;


onMount(()=>{
window.onscroll = function() {myFunction()};

var header = document.getElementById("mainHeader");
console.log(header)
var sticky = header.offsetTop;

function myFunction() {
  console.log(header,window.pageYOffset,sticky,header.classList)
  if (window.pageYOffset > sticky) {
    header.classList.add("sticky");
  } else {
    header.classList.remove("sticky");
  }
  console.log(window.pageYOffset > sticky,header.classList)
}


// make the string html compatible
var el = document.getElementById('logo')
el.innerText = el.textContent = '[]{} §0d|3a|1n|0[--]i|2e|1l|1 |0e|2l|1l|3i|1s|3[+]'
var el = document.getElementById('logo2')
// el.innerText = el.textContent = ' §3r|2[++]e|2s|0e|1a|3r|2c|1h '

//'[contracting]{[--]}  d|2a|1n|3i|2e|2l|1 |1e|2l|0l|3i|1[++]s|1   [ [research]]'

// '[]{[--]} §0d|3a|2n|1i|2e|0l|0 |0e|1l|0l|2i|1[++]s|3 |1 { }{ }{ }{ }{ }{ }{ }{ }{ }{ }{[ \[research.com]\]}'
// '[]{[--]} d|2a|0n|3i|2e|2l|1 |0e|1l|0l|2i|1[++]s|3 |1[[]]'

//origi
// []{[--]}  d|2a|1n|3i|2e|2l|1 |1e|2l|0l|3i|1[++]s|1   [ []]
})


</script>

<main>
  <div class="top-container">
    <slot></slot>
  </div>
    <header>

  


  <div class="sticky-nav" id='mainHeader'>
    <a id="mobile-nav" class="menu-nav" href="#menu-nav" />
    <div id="logo" class='logo'>
      <!-- <h4 style="font-size:130% ">Daniel Ellis Research</h4> -->
    </div><div id="logo2" class='logo'></div>


    <nav id="menu">
      <!-- <a id="goUp" href="#home-slider" <="" a="" /> -->
      <ul id="menu-nav">


        {#each menu as link}
        <li class = {(window.location.origin == link.href)?'current':''}><a href="{link.href}">{link.name}</a></li>
        {/each}

    </nav>
  </div>
</header>


</main>

<style>




@font-face {
	font-family: 'Datalegreya-Dot';
	src: url('/Datalegreya-Dot.otf');
	font-weight: normal;
	font-style: normal;
}

.logo{
  font-family: Datalegreya-Dot;
  font-size:130%;
	-webkit-font-feature-settings: "kern" on, "liga" on, "calt" on;
	-moz-font-feature-settings: "kern" on, "liga" on, "calt" on;
	-webkit-font-feature-settings: "kern" on, "liga" on, "calt" on;
	-ms-font-feature-settings: "kern" on, "liga" on, "calt" on;
	font-feature-settings: "kern" on, "liga" on, "calt" on;
	font-variant-ligatures: common-ligatures discretionary-ligatures contextual;
	text-rendering: optimizeLegibility;
	-webkit-font-smoothing: antialiased;
	-moz-osx-font-smoothing: grayscale;
  margin-left: 10px !important;
  padding-top: 10px!important;
  padding-bottom: 10px!important;
  float: left;

}

#logo {
  font-size:130%;

}
#logo2 {
  vertical-align: text-bottom;
  left:0;
  bottom: 0%;
  margin-top: auto!important;
  font-family: Datalegreya-Dot;
  font-size:50%;

}

header {
  top:0;
  display:block;

}

:global(body){
  margin: auto !important;
  padding-top: 10px;
  padding-bottom: 10px;
  
}
:global(.top-container) {
  /* background-color: #f1f1f1; */
  /* padding-bottom: 130px; */
  position: relative;
  padding:20px;
  height:auto;
  text-align: center;
  overflow-x: hidden;
  overflow-y: hidden;
}

.sticky-nav{
  left:0!important;
  /* position:absoulte; */
  margin-left: 0;
  padding-left: 0;
  width:100vw;
  font-family: Datalegreya-Dot;
  font-size: 230%!important;
  /* position: relative; */
}

li{

  text-rendering: optimizeLegibility;
	-webkit-font-smoothing: antialiased;
	/* -moz-osx-font-smoothing: grayscale; */
  font-weight: 800;
}

li a{
  
  font-size: .65em!important;
  display:inline-block;
}
/* .content {
  padding: 16px;
} */

:global(.sticky) {
  position: fixed!important;
  left:0;
  top: 0!important;
  /* width: 100%; */
}

.sticky + .content {
  padding-top: 202px;
}

:global(html) {
  scroll-behavior: smooth;
}


h1, h2, h3, h4, h5, h6 {
    margin: 0 0 15px;
    color: #fff;
    font-weight: 300;
    font-family: open sans,sans-serif;
    line-height: 1.5em;
}
</style>

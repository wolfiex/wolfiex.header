
<style>
    @font-face {
    font-family: 'Datalegreya-Dot';
    src: url('/Datalegreya-Dot.otf');
    font-weight: normal;
    font-style: normal;
  }

  :global(a#nav-toggles){
    /* background:rgba(0, 136, 255, 0.1);
     */
    
    backdrop-filter: blur(10px);
    border-left: 3px double rgba(245, 245, 245, 0.226);
  }
  :global(a#nav-toggles>span.material-symbols-outlined){
    /* color: rgb(251, 78, 15)!important;
     */
     color:rgb(4, 183, 240)
  }

  :global(.sticky) {
    position: fixed !important;
    display:block!important;
    z-index: 99999!important;
    left: 0!important;
    top: 0 !important;
    /* filter:invert(1)!important; */
    /* width: 100%; */
  }
</style>



<script>
  import './header.css'
  import {onMount} from 'svelte';
  import {
    Button,
    ButtonSet,
  } from 'carbon-components-svelte';
  import 'carbon-components-svelte/css/g90.css';
  // import './css/header.css';
  import Nav from './Nav.svelte'

  
  // header style
  export let style = 'transparent'
  var fstyle = '#222'
  var bstyle = 'whitesmoke'


  console.error(style)
  switch(style) {
  case "dark":
    bstyle = "background: rgb(38, 41, 46)!important;"
    fstyle = "color:rgb(214, 214, 214)!important";
    break;
  case "light":
    bstyle = "background:whitesmoke!important;border-top: .2px solid gray;backdrop-filter: blur(10px);"
    fstyle = "color:#222;";
    break;
    case "active":
    bstyle = "background:whitesmoke!important;border-top: .2px solid gray;backdrop-filter: blur(10px);margin-top:0em!important"
    fstyle = "color:#222;";
    break;
  case "transparent":
    bstyle = 'background: rgba(255,255,255,.051);backdrop-filter: blur(5px);'
    fstyle = "color:rgb(214, 214, 214)"
    break;
  }


  let w;
  const host = 'danielellisresearch.com';
  const menu = [
    // {href:'#', name:''},
    {href: 'https://showcase.' + host, name: 'Showcase',icon:'collections_bookmark'},
    {href: 'https://medium.' + host, name: 'Published-Articles',icon:'history_edu'},
    {href: 'https://research.' + host, name: 'Academic',icon:'school',disabled:true},
    {href: 'https://coaching.' + host, name: 'Adventure-Instructing',icon:'rocket_launch'},
    {href: 'https://art.' + host, name: 'Art',icon:
'palette',disabled:true},

    {href:'mailto:contact@danielellisresearch.com?subject=Website Query"', name: ' Contact',icon:'mail'}, // cv
  ];

  onMount(() => {
    window.onscroll = function () {
      isSticky();
    };

    //

    var header = document.getElementById('mainHeader');
    var sticky = header.offsetTop;

    function isSticky() {
      if (window.pageYOffset > sticky) {
        header.classList.add('sticky');
      } else {
        header.classList.remove('sticky');
      }
      console.log(window.pageYOffset > sticky, header.classList,header);
    }

    // make the string html compatible
    var el = document.getElementById('logo');
    el.innerText = el.textContent =
    '[]{[--]}  d|2a|1n|3i|2e|2l|1 |1e|2l|0l|3i|1[++]s|1   [ []]'
     // '[]{} §0d|3a|1n|0[--]i|2e|1l|1 |0e|2l|1l|3i|1s|3[+]';
   
  });
</script>

<svelte:window bind:innerWidth={w} />
<svelte:head>
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0"
  />
</svelte:head>
<main>
  <div class="top-container">
    <slot />
  </div>
  <danheader>
    <div class="sticky-nav" id="mainHeader"  style = {'height:3.5em;'+bstyle} >
      <a href="https://danielellisresearch.com" >
      <div id="logo" class="logo" style = {fstyle}>
      </div>
    </a>

     


        {#if w > 660}
          <div style={"float:right;display:inline-block" + bstyle}>
            {#each menu as link}
              <Button
                style={"width:auto;"+fstyle}
                kind="ghost"
                iconDescription={link.name}
                href={link.href}
                disabled={link.disabled}
               
                ><span class="material-symbols-outlined">
                  {link.icon||'rocket_launch'}
                  <!-- rocket_launch -->
                </span></Button
              >
            {/each}
          
            <Button
                style="width:auto;"
                kind="ghost"
                iconDescription='Toggle Nav'
                href={'#'}
                id="nav-toggles" 
                on:click={function(d) {
                  document.getElementById('nav-menu').classList.toggle("active");
                  console.error('ppp',document.getElementById('nav-menu').classList)
                }}
                ><span class="material-symbols-outlined">
                  {'menu'}
                  <!-- rocket_launch -->
                </span></Button
              >
          </div>
          

          <!-- {:else} -->
        {/if}
        
        <!-- <Nav menu={menu}/> -->

    </div>
  </danheader>
</main>

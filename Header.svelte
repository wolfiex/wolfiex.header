
<style>
  @font-face {
    font-family: 'Datalegreya-Dot';
    src: url('/Datalegreya-Dot.otf');
    font-weight: normal;
    font-style: normal;
  }

  :global(.overflow) {
    font-size: x-small;
    display: inline-block;
    margin: auto;
    border-color: rgb(37, 35, 35);
    border: 2px;
    border-style: groove;
    float: right !important;
    right: 0;
    position: relative;
  }
  :global(#overflowbtn) {
    background-color: rgba(173, 190, 190, 0.053);
    border: 2px;
    /* border-style: groove; */
  }
  .logo {
    font-family: Datalegreya-Dot;
    font-size: 130%;
    -webkit-font-feature-settings: 'kern' on, 'liga' on, 'calt' on;
    -moz-font-feature-settings: 'kern' on, 'liga' on, 'calt' on;
    -webkit-font-feature-settings: 'kern' on, 'liga' on, 'calt' on;
    -ms-font-feature-settings: 'kern' on, 'liga' on, 'calt' on;
    font-feature-settings: 'kern' on, 'liga' on, 'calt' on;
    font-variant-ligatures: common-ligatures discretionary-ligatures contextual;
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    margin-left: 10px !important;
    padding-top: 10px !important;
    padding-bottom: 1px !important;
    float: left;
  }

  #logo {
    font-size: 130%;
  }
  #logo2 {
    vertical-align: text-bottom;
    left: 0;
    bottom: 0%;
    margin-top: auto !important;
    font-family: Datalegreya-Dot;
    font-size: 50%;
  }

  header {
    top: 0;
    display: block;
  }

  :global(a){
    color:rgb(214, 214, 214)!important;
  }
  :global(a:hover){
    color:#4856fd!important;
  }
  :global(a.bx--btn--ghost:hover){
    background-color:rgba(30, 28, 33, 0.87)
  }
  
  :global(body) {
    margin: auto !important;
    padding-top: 10px;
    padding-bottom: 10px;
  }
  :global(.top-container) {
    /* background-color: #f1f1f1; */
    /* padding-bottom: 130px; */
    position: relative;
    padding: 20px;
    height: auto;
    text-align: center;
    overflow-x: hidden;
    overflow-y: hidden;
  }

:global(main){
  max-width:none;
}
  .sticky-nav {
    left: 0 !important;
    /* position:absoulte; */
    margin-left: 0;
    padding-left: 0;
    width: 100vw;
    font-family: Datalegreya-Dot;
    font-size: 230% !important;
    /* position: relative; */
  }

  li {
    text-rendering: optimizeLegibility;
    -webkit-font-smoothing: antialiased;
    /* -moz-osx-font-smoothing: grayscale; */
    font-weight: 800;
  }

  li a {
    font-size: 0.65em !important;
    display: inline-block;
  }
  /* .content {
  padding: 16px;
} */

  :global(.sticky) {
    position: fixed !important;
    left: 0;
    top: 0 !important;
    /* width: 100%; */
  }

  .sticky + .content {
    padding-top: 202px;
  }

  :global(html) {
    scroll-behavior: smooth;
  }

  h1,
  h2,
  h3,
  h4,
  h5,
  h6 {
    margin: 0 0 15px;
    color: #fff;
    font-weight: 300;
    font-family: open sans, sans-serif;
    line-height: 1.5em;
  }

  .material-symbols-outlined {
    font-variation-settings: 'FILL' 0, 'wght' 400, 'GRAD' 0, 'opsz' 48;
  }
</style>



<script>
  import {onMount} from 'svelte';
  import {
    OverflowMenu,
    OverflowMenuItem,
    Button,
    ButtonSet,
  } from 'carbon-components-svelte';
  import 'carbon-components-svelte/css/g90.css';
  import './css/header.css';

  let w;
  const host = 'danielellisresearch.com';
  const menu = [
    // {href:'#', name:''},
    {href: 'https://showcase.' + host, name: 'Showcase',icon:'collections_bookmark'},
    {href: 'https://medium.' + host, name: 'Published-Articles',icon:'history_edu'},
    {href: 'https://research.' + host, name: 'Academic',icon:'school',disabled:true},
    {href: 'https://coaching.' + host, name: 'Adventure-Instrucing',icon:'rocket_launch'},
    {href: 'https://art.' + host, name: 'Art',icon:
'palette',disabled:true},

    {href:'mailto:contact@danielellisresearch.com?subject=Website Query"', name: ' Contact',icon:'mail'}, // cv
  ];

  onMount(() => {
    window.onscroll = function () {
      myFunction();
    };

    //

    var header = document.getElementById('mainHeader');
    // console.log(header);
    var sticky = header.offsetTop;

    function myFunction() {
      // console.log(header, window.pageYOffset, sticky, header.classList);
      if (window.pageYOffset > sticky) {
        header.classList.add('sticky');
      } else {
        header.classList.remove('sticky');
      }
      // console.log(window.pageYOffset > sticky, header.classList);
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
  <header>
    <div class="sticky-nav" id="mainHeader">
      <a href="https://danielellisresearch.com" >
      <div id="logo" class="logo">
      </div>
    </a>

      {#if w > 1100}
        <nav id="menu">
          <ul id="menu-nav">
            {#each menu as link}
              <li class={window.location.origin == link.href ? 'current' : ''}>

                <a href={link.href}>{link.name}</a>
              </li>
            {/each}
          </ul>



        </nav>
      {:else}
        <div class="overflow">
          <OverflowMenu
            flipped
            size="xl"
            iconDescription="View Menu Items"
            id="overflowbtn"
          >
            {#each menu as link}
              <OverflowMenuItem href={link.href} text={link.name} />
            {/each}
          </OverflowMenu>
          menu
        </div>
        {#if w > 660}
          <div style="float:right;display:inline-block">
            {#each menu as link}
              <Button
                style="width:auto;"
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
          </div>
          <!-- {:else} -->
        {/if}
      {/if}
    </div>
  </header>
</main>

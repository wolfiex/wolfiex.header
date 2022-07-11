
<svelte:window bind:innerWidth={w} />
<svelte:head>
  <!-- <link rel="preload" href="/Datalegreya-Dot.otf" as="font" type="font/otf" crossorigin> -->
  <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0"
  />
</svelte:head>

<style>

@font-face {
    font-family: 'Datalegreya-Dot';
    src: url('/Datalegreya-Dot.woff2');
    font-weight: normal;
    font-style: normal;
  }

</style>



<script>
  import './header.css'
  import {onMount} from 'svelte';
  import {
    OverflowMenu,
    OverflowMenuItem,
    Button,
    ButtonSet,
  } from 'carbon-components-svelte';
  import 'carbon-components-svelte/css/g90.css';
  import './css/header.css';

  

  
  // header style
  export let style = 'transparent';
  export let loading=false;

  console.error(style)
  switch(style) {
  case "dark":
    style = "background: rgb(38, 41, 46);color:rgb(214, 214, 214);backdrop-filter: blur(10px)";
    break;
  case "light":
    style = "background: rgb(254, 254, 254,.7);color:#222;backdrop-filter: blur(10px)";
    break;
  case "transparent":
    style = 'background: rgba(255,255,255,.051);backdrop-filter: blur(5px);color:rgb(214, 214, 214)'
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


    document.fonts.ready.then(function () {
  // alert('All fonts in use by visible text have loaded.');
  //  alert('DLG loaded? ' + document.fonts.check('1em Datalegreya-Dot'));  // true

  if (document.fonts.check('1em Datalegreya-Dot')){
    loading = true;
    console.warn('finished loading fonts')

  }
});

// document.fonts.onloadingdone = function (fontFaceSetEvent) {
//    alert('onloadingdone we have ' + fontFaceSetEvent.fontfaces.length + ' font faces loaded');
// };


    // make the string html compatible
    var el = document.getElementById('logo');
    el.innerText = el.textContent =
    '[]{[--]}  d|2a|1n|3i|2e|2l|1 |1e|2l|0l|3i|1[++]s|1   [ []]'
     // '[]{} §0d|3a|1n|0[--]i|2e|1l|1 |0e|2l|1l|3i|1s|3[+]';
   
  });
</script>

<main>
  <div class="top-container">
    <slot />
  </div>
  <header >
    <div class="sticky-nav" id="mainHeader" style = {style}>
      <a href="https://danielellisresearch.com" >
      <div id="logo" class="logo"> Daniel Ellis Research
      </div>
    </a>

     
   
        <!-- <div class="overflow">
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
        </div> -->



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

    </div>
  </header>
</main>

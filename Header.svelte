<script>
  import './header.css';
  import {onMount} from 'svelte';
  import {Button, ButtonSet, Link} from 'carbon-components-svelte';
  import 'carbon-components-svelte/css/g90.css';
  import Nav from './Nav.svelte';

  // header style
  export let style = 'transparent';
  export let loaded = false;
  let scrollY = 0;
  let header, sticky;
  let open = true;

  var fstyle = '#222';
  var bstyle = 'whitesmoke';

  let w, h, mobile;

  switch (style) {
    case 'dark':
      bstyle = 'background: rgb(38, 41, 46)!important;';
      fstyle = 'color:rgb(214, 214, 214)!important;';
      break;
    case 'light':
      bstyle =
        'background:whitesmoke!important;border-top: .2px solid gray;backdrop-filter: blur(10px);';
      fstyle = 'color:#222;';
      break;
    case 'active':
      bstyle =
        'background:whitesmoke!important;border-top: .2px solid gray;backdrop-filter: blur(10px);margin-top:0em!important;';
      fstyle = 'color:#222;';
      break;
    case 'transparent':
      bstyle = 'background: rgba(255,255,255,.02);backdrop-filter: blur(5px);';
      fstyle = 'color:rgb(214, 214, 214);';
      break;
  }

  const host = 'danielellisresearch.com';
  const menu = [
    // {href:'#', name:''},
    {
      href: 'https://showcase.' + host,
      name: 'Showcase',
      icon: 'reviews',
    },
    {
      href: 'https://medium.' + host,
      name: 'Published Articles',
      icon: 'history_edu',
    },
    {
      href: 'https://research.' + host,
      name: 'Academic',
      icon: 'school',
      disabled: true,
    },
    {
      href: 'https://coaching.' + host,
      name: 'Adventure / Instructing',
      icon: 'rocket_launch',
      disabled: true,
    },
    {
      href: 'https://showcase.' + host,
      name: 'Art',
      icon: 'palette',
      disabled: false,
    },

    {
      href: 'mailto:contact@danielellisresearch.com?subject=Website Query"',
      name: ' Contact',
      icon: 'mail',
    }, // cv
  ];

  onMount(() => {
    try {
      mobile = navigator.userAgentData.mobile;
    } catch (err) {
      mobile = w < 600;
    }
    // console.error(mobile,'mobile')
    // console.log(header);
    sticky = header.offsetTop;

    var el = document.getElementById('logo');
    el.innerText = el.textContent =
      '[]{[--]}  d|2a|1n|3i|2e|2l|1 |1e|2l|0l|3i|1[++]s|1   [ []]';
    // '[]{} §0d|3a|1n|0[--]i|2e|1l|1 |0e|2l|1l|3i|1s|3[+]';
  });
</script>

<svelte:head>
  <!-- load the font early  -->
  <link
    rel="stylesheet"
    href="/Datalegreya-Dot.woff2"
    as="font"
    type="font/woff"
    crossorigin="anonymous"
  />
  <!--  add above to layout  -->
  <!-- as="Datalegreya-Dot" -->

  <title>Daniel Ellis Research</title>
  <!-- <link
    rel="stylesheet"
    href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0"
  /> -->
</svelte:head>

<svelte:window bind:innerWidth={w} bind:innerHeight={h} bind:scrollY />

<main>
  <div class="top-container" style="max-height:700px;overflow:clip;">
    <slot />
  </div>

  <Nav {menu} open={false} />
  <danheader>
    <div
      class="sticky-nav"
      class:sticky={scrollY > sticky}
      id="mainHeader"
      bind:this={header}
      style={'height:2.75rem;' + bstyle}
    >
      <a
        href="https://danielellisresearch.com"
        style="float:left!important;"
        class:head={mobile}
      >
        <div id="logo" class="logo" class:top={mobile} style={fstyle}>
          
        </div>
      </a>

      <!-- {#if w > 660} -->
      <div
        style={'float:right;display:inline-block;height:2rem' + bstyle}
        class:footer={mobile}
      >
        {#each menu as link}
          <Button
            style={'width:auto;' + fstyle}
            kind="ghost"
            iconDescription={link.name}
            href={link.href}
            disabled={link.disabled}
            ><img
              src={'/icons/' + link.icon + '.svg'}
              class="material-symbols-outlined"
            />
            <!-- {link.icon || 'rocket_launch'} -->
            <!-- rocket_launch -->
          </Button>
        {/each}

        {#if !mobile}
          <Button
            style="width:auto;"
            kind="ghost"
            iconDescription="Toggle Nav"
            href={'#'}
            id="nav-toggles"
            on:click={function (d) {

              alert('Navigation menu temporarily disabled. ')

              // document.getElementById('nav-menu').classList.toggle('active');
              // document.getElementById('mainBox').classList.toggle('fixed');
              // open = document
              //   .getElementById('nav-menu')
              //   .classList.contains('active');

              // console.error('ppp', document.getElementById('nav-menu').classList);
            }}
            ><img
              class="material-symbols-outlined"
              src="/icons/menu.svg"
              style="stroke: #78a9ff!important;"
            />

            <!-- rocket_launch -->
          </Button>
        {/if}
      </div>

      <!-- {:else} -->
      <!-- {/if} -->

      <!-- <Nav menu={menu}/> -->
    </div>
  </danheader>
</main>

<style>
  /* @font-face {
    font-family: 'Datalegreya-Dot';
    src: url('/Datalegreya-Dot.woff2');
    font-weight: normal;
    font-style: normal;
    font-display: swap;
  } */

  danheader {
    z-index: 999999 !important;
  }

  .top {
    top: -1.2em !important;
    position: absolute;
    display: block;
  }
  :global(a#nav-toggles) {
    backdrop-filter: blur(10px);
    border-left: 3px double rgba(245, 245, 245, 0.226);
  }
  :global(a#nav-toggles > span.material-symbols-outlined) {
    /* color: rgb(251, 78, 15)!important;
     */
    color: rgb(4, 183, 240);
  }

  :global(.sticky) {
    position: fixed !important;
    display: block !important;
    z-index: 9999 !important;
    left: 0 !important;
    top: 0 !important;
    /* filter:invert(1)!important; */
    /* width: 100%; */
  }

  .footer {
    clear: both !important;
    display: block !important;
    position: fixed !important;

    bottom: calc(100vh-3.5em) !important;
    /* bottom:.5em!important; */
    width: 100% !important;
    float: right !important;
    margin-left: auto;
    right: 2px !important;
  }

  .footer::before {
    content: '\A\A';
    white-space: pre-lines;
  }
  .head {
    top: 2px !important;
    position: absolute;
    display: block;
    width: 100%;
  }

  .material-symbols-outlined {
    fill: red;
    width: 100%;
    height: 1.5rem;
  }

  :global(#logo) {
    font-size:2.5rem!important;
    top:-.25rem!important;
    font-family: Datalegreya-Dot !important;
  }
</style>

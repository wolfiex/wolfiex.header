<script>
import { onMount } from "svelte";


  // import {Link} from 'carbon-components-svelte';
  // import {onMount} from 'svelte';

  export let menu = false;
  export let open = true;
  console.log('startnav');


  $: console.log(menu);
</script>


<nav id="nav-menu" class:active={open} >
  <div class="container-fluid">
    <div class="row">
      <div
        class="col-md-8 col-md-offset-2 col-sm-8 col-sm-offset-2 col-xs-8 col-xs-offset-2"
      >
        <div class="pull" >
          <ul class="top-nav">
            {#if menu != false}
              {#each menu as link}
                <li>
                  <a href={link.href}>
                   

                    
                    <span style='margin-left:1em;vertical-align: middle!important;'><i class="fa fa-angle-right" /> {link.name}</span>

                    <span class="material-symbols-outlined" style="float:right;vertical-align:middle;font-size: 1em;"> 
                      keyboard_arrow_right
                      </span>
                  </a>
                </li>
              {/each}
            {/if}
          </ul>
        </div>
      </div>
    </div>
  </div>

</nav>

<style>


  nav {
    /* position: absolute; */
    display: block;
    width: 100%;
    font-size: large;
    opacity: 0.8!important;
  }
  nav:parent {
    all: revert;
  }

  .container-fluid{
    width:60%;
    margin:auto;
  }

  ul{
    pointer-events: auto;
  }
  :global(#nav-menu:not(.active)) {
    opacity: 1;
    display: none;
  }
  :global(#nav-menu.active) {
    /* This section calls the slideInFromLeft animation we defined above */
    display: block;
    opacity: 1;
    animation: 1s ease-in 0s 1 slideIn;
    backdrop-filter: blur(10px);
  }

  /* ==========================================================================
Navigation
========================================================================== */
  nav {
    background-color: #242830;
    margin-top: -1px;
  }
  nav ul {
    list-style: none;
    padding: 0;
  }
  nav ul li {
    color: rgba(255, 255, 255, 0.6);
    display: block;
    border-bottom: 1px dotted rgba(255, 255, 255, 0.2);
    transition: all 0.5s ease;
    -moz-transition: all 0.5s ease;
    -webkit-transition: all 0.5s ease;
    -o-transition: all 0.5s ease;
    padding-left: 0;

    position: relative;
  }

  nav ul li:last-child {
    border: none;
  }
  nav ul li a {
    color: rgba(255, 255, 255, 0.6);
    display: block;
    padding: 20px;
    transition: all 0.5s ease;
    -moz-transition: all 0.5s ease;
    -webkit-transition: all 0.5s ease;
    -o-transition: all 0.5s ease;
    padding-left: 0;
    position: relative;
  }
  nav ul li a:hover,
  nav ul li a:focus {
    text-decoration: none;
    color: rgba(255, 255, 255, 1);
  }

  /* .pull { display: none; } */

  .fa {
    display: inline-block;
    font-family: FontAwesome;
    font-style: normal;
    font-weight: normal;
    line-height: 1;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

nav ul, nav ol { list-style: none; list-style-image: none; }

dl, menu, ol, ul { margin: 1em 0; }
menu, ol, ul { padding: 0 0 0 40px; }

</style>

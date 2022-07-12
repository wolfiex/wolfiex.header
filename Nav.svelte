<script>
  import {Link} from 'carbon-components-svelte';
  import {onMount} from 'svelte';

  export let menu = false;
//   onMount(() => {
//     console.log(menu);
//   });

  $: console.log(menu);
</script>

<nav id="nav-menu">
  <div class="container-fluid">
    <div class="row">
      <div
        class="col-md-8 col-md-offset-2 col-sm-8 col-sm-offset-2 col-xs-8 col-xs-offset-2"
      >
        <div class="pull">
          <ul class="top-nav">
            {#if menu != false}
              {#each menu as link}
                <li>
                  <a href={link.href}>
                    {link.name}
                    <span><i class="fa fa-angle-right" /></span>
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
  }
  /* nav:parent{all: revert;} */

  :global(#nav-menu:not(.active)) {
    opacity: 0;
    display: none;
  }
  :global(#nav-menu.active) {
    /* This section calls the slideInFromLeft animation we defined above */
    display: inline;
    opacity: 1;
    animation: 1s ease-in 0s 1 slideIn;
  }
</style>

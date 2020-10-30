<script>
    import { links } from "svelte-routing";
    export let to;
  </script>
  
  <style>
    .button {
      background: grey;
    }
    .button:hover,
    .button:focus {
      filter: brightness(115%);
      outline: none;
      text-decoration: none;
    }
  </style>
  
  {#if to}
    <a href={to} on:click use:links class="button">
      <slot />
    </a>
  {:else}
    <button on:click class="button">
      <slot />
    </button>
  {/if}
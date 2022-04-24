<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();
  export let tabs;
  export let activeTab;
</script>

<div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
  <div class="text-sm font-medium text-center text-gray-500 border-b border-gray-200 dark:text-gray-400 dark:border-gray-700">
    <ul class="flex flex-wrap -mb-px">
      {#each tabs as tab}
        <li class="mr-2" on:click|preventDefault="{() => dispatch('tabChange', tab)}">
          <a href="/" class:active="{tab === activeTab}" class="inline-block p-4 rounded-t-lg border-b-2 border-transparent hover:text-gray-600 hover:border-gray-300"> <span> {tab}</span></a>
        </li>
      {/each}
    </ul>
  </div>
</div>

<style>
  .active {
    @apply border-b-2 border-red-500;
  }
</style>

<script>
  import { onDestroy } from "svelte";
  import SkinStore from "../stores/SkinStore.ts";
  import SkinDetails from "./SkinDetails.svelte";
  export let skins = [];

  const unsubFromStore = SkinStore.subscribe((data) => {
    skins = data;
  });

  onDestroy(() => {
    unsubFromStore();
  });
</script>

<div class="container px-5 py-24 mx-auto">
  <div class="flex flex-wrap w-full mb-20">
    <div class="lg:w-1/2 w-full mb-6 lg:mb-0">
      <h1 class="sm:text-3xl text-2xl font-medium title-font mb-2 text-gray-900">All skins</h1>
      <div class="h-1 w-20 bg-indigo-500 rounded"></div>
    </div>
  </div>
  <div class="flex flex-wrap -m-4">
    {#each skins as skin (skin.id)}
      <SkinDetails skin="{skin}" />
    {/each}
  </div>
</div>

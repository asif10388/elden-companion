<script lang="ts">
  import Counter from "./comps/Counter.svelte";
</script>

<main>
  <div class="container px-5 py-24 mx-auto">
    <div class="flex justify-center flex-wrap -mx-4 -mb-10 text-center">
      <div class="w-full mb-10 px-4">
        <h2 class="title-font text-7xl font-medium text-gray-900 mt-6 mb-3">Hello Tailwind + TypeScript!</h2>
        <Counter />
      </div>
    </div>
  </div>
</main>

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>

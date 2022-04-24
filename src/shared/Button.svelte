<script>
  export let type = "primary";
</script>

<button on:click>
  <slot />
</button>

<style>
  button {
    @apply flex mx-auto text-white bg-green-500 border-0 py-2 px-8 rounded text-lg;
  }
</style>

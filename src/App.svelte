<script lang="ts">
  import Header from "./comps/Header.svelte";
  import Footer from "./comps/Footer.svelte";
  import Tabs from "./shared/Tabs.svelte";
  import CreateSkin from "./comps/CreateSkin.svelte";
  import SkinList from "./comps/SkinList.svelte";

  let tabs = ["Current Skins", "All Skins", "New Skin"];
  let activeTab = "Current Skins";

  const tabChange = (e) => {
    activeTab = e.detail;
    console.log(e.detail);
  };

  function handleAddSkin(e) {
    activeTab = "Current Skins";
  }
</script>

<Header />
<main>
  <Tabs activeTab="{activeTab}" tabs="{tabs}" on:tabChange="{tabChange}" />

  {#if activeTab === "Current Skins"}
    <SkinList />
  {:else if activeTab === "New Skin"}
    <h1><CreateSkin on:createSkin="{handleAddSkin}" /></h1>
  {/if}
</main>
<Footer />

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>

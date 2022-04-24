<script>
  import SkinStore from "../stores/SkinStore.ts";
  import Button from "../shared/Button.svelte";
  export let skin;

  const handleVote = (vote, id) => {
    SkinStore.update((currentSkins) => {
      let updatedSkins = [...currentSkins];
      let updatedSkinVote = updatedSkins.find((skin) => skin.id === id);

      if (vote === "up") {
        updatedSkinVote.upVote++;
      }

      if (vote === "down") {
        updatedSkinVote.downVote++;
      }

      return updatedSkins;
    });
  };

  const handleDelete = (id) => {
    SkinStore.update((currentSkins) => {
      return currentSkins.filter((skin) => skin.id !== id);
    });
  };
</script>

<div class="xl:w-1/4 md:w-1/2 p-4">
  <div class="bg-gray-100 p-6 rounded-lg">
    <img class="h-40 rounded w-full object-cover object-center mb-6" src="https://dummyimage.com/723x403" alt="content" />
    <h3 class="tracking-widest text-indigo-500 text-xs font-medium title-font">{skin.createdAt}</h3>
    <h2 class="text-lg text-gray-900 font-medium title-font mb-4">{skin.name}</h2>
    <p class="leading-relaxed text-base">No Description.</p>
    <div class="flex items-center flex-wrap ">
      <span on:click="{() => handleVote('up', skin.id)}" class="text-gray-400 mr-3 inline-flex items-center leading-none text-sm pr-3 py-1 border-r-2 border-gray-200">
        {skin.upVote}
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-8.707l-3-3a1 1 0 00-1.414 0l-3 3a1 1 0 001.414 1.414L9 9.414V13a1 1 0 102 0V9.414l1.293 1.293a1 1 0 001.414-1.414z" clip-rule="evenodd"></path>
        </svg>
      </span>
      <span on:click="{() => handleVote('down', skin.id)}" class="text-gray-400 inline-flex items-center leading-none text-sm">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" viewBox="0 0 20 20" fill="currentColor">
          <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-11a1 1 0 10-2 0v3.586L7.707 9.293a1 1 0 00-1.414 1.414l3 3a1 1 0 001.414 0l3-3a1 1 0 00-1.414-1.414L11 10.586V7z" clip-rule="evenodd"></path>
        </svg>
        {skin.downVote}
      </span>
    </div>
    <Button on:click="{() => handleDelete(skin.id)}">Delete</Button>
  </div>
</div>

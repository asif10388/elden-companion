<script>
  import SkinStore from "../stores/SkinStore.ts";
  import { createEventDispatcher } from "svelte";
  import { nanoid } from "nanoid";
  let dispatch = createEventDispatcher();
  import Button from "../shared/Button.svelte";
  let fields = {
    name: "",
    description: "",
    image: "",
    category: "",
    tags: "",
  };

  let errors = {
    name: "",
    description: "",
    image: "",
    category: "",
    tags: "",
  };

  let valid = false;

  const handleSubmit = (e) => {
    e.preventDefault();
    valid = true;

    if (fields.name === "") {
      valid = false;
      errors.name = "Name is required";
    } else errors.name = "";
    if (fields.image === "") {
      valid = false;
      errors.image = "Image is required";
    } else errors.image = "";

    if (valid) {
      let newSkin = { ...fields, upVote: 0, downVote: 0, createdAt: new Date(), id: nanoid() };
      SkinStore.update((skins) => [newSkin, ...skins]);
      dispatch("createSkin");
    }
  };
</script>

<section class="text-gray-600 body-font relative">
  <div class="container px-5 py-24 mx-auto">
    <div class="flex flex-col text-center w-full mb-12">
      <h1 class="sm:text-3xl text-2xl font-medium title-font mb-4 text-gray-900">Create Skin</h1>
    </div>
    <div class="lg:w-1/2 md:w-2/3 mx-auto">
      <div class="flex flex-col flex-wrap -m-2 items-center">
        <div class="p-2 w-1/2">
          <div class="relative">
            <label for="name" class="leading-7 text-sm text-gray-600">Skin Name</label>
            <input type="text" class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" bind:value="{fields.name}" />
            <div class="text-red-500">{errors.name}</div>
          </div>
        </div>
        <div class="p-2 w-1/2">
          <div class="relative">
            <label for="image" class="leading-7 text-sm text-gray-600">Skin Image</label>
            <input type="text" class="w-full bg-gray-100 bg-opacity-50 rounded border border-gray-300 focus:border-indigo-500 focus:bg-white focus:ring-2 focus:ring-indigo-200 text-base outline-none text-gray-700 py-1 px-3 leading-8 transition-colors duration-200 ease-in-out" bind:value="{fields.image}" />
            <div class="text-red-500">{errors.image}</div>
          </div>
        </div>
        <div class="p-2 w-full">
          <Button on:click="{handleSubmit}">Submit</Button>
        </div>
      </div>
    </div>
  </div>
</section>

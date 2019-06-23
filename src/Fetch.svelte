<script>
  import { onMount } from "svelte";

  // props
  export let url = "url.com";
  export let searchTerm = undefined;

  // filter data
  let jsonResponse = [];
  $: regex = new RegExp(searchTerm, "gi");
  $: data = searchTerm ? jsonResponse.filter(el => el.name.match(regex)) : jsonResponse;

  onMount(async function() {
    const response = await fetch(url);
    const json = await response.json();
    jsonResponse = json;
  });
</script>

<slot {data} />
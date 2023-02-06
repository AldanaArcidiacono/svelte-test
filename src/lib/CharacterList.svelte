<script lang="ts">
  import { onMount } from "svelte";
  import type { Result } from "../models/characters";

  let characters: Result[] = [];

  onMount(async () => {
    const response = await fetch("https://rickandmortyapi.com/api/character");
    const data = await response.json();
    characters = data.results;
  });
</script>

<ul>
  {#each characters as character}
    <li>
      <p>{character.name}</p>
      <img src={character.image} alt={character.name} />
    </li>
  {/each}
</ul>

<script>
import { onMount } from 'svelte';
import { navigate } from 'svelte-routing'
import { fade } from 'svelte/transition'

import SearchResult from './../components/SearchResult.svelte'

export let results;
export let query;

export const addResult = (result) => {
  results = [...results, result];
};

onMount(() => {
  console.log('query: ', query)
  if (!query) navigate('/');
})

</script>

<div class="search-results" in:fade={{ delay: 200, duration: 200 }} out:fade={{ duration: 200 }}>
  <div class="search-results-query">
    {#if results.length > 0}
      Search results for "{query}"
    {:else}
      No results for "{query}"
    {/if}
  </div>
  <div class="search-results-list">
    {#each results as result}
      <SearchResult {...result} />
    {/each}
  </div>
</div>

<style lang="stylus">
.search-results
  &-query
    font-size 2.5rem
    font-weight bold
</style>
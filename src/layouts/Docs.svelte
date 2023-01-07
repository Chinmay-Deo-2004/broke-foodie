<script>
import { fade } from 'svelte/transition'

</script>

<div class="docs" in:fade={{ delay: 200, duration: 200 }} out:fade={{ duration: 200 }}>
  <h1>
    How to use BrokeFoodie?
  </h1>
  <br />
  <p>Hang tight! Docs coming soon.</p>

</div>
<style lang="stylus">
.docs
  h1
    font-size 2rem
  p
    font-size 1rem
</style>
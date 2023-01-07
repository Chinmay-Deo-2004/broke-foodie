<script>
import { navigate } from 'svelte-routing'

const links = [
  {name: 'search-results', text: 'Search'},
  {name: 'about', text: 'About Us'},
  {name: 'docs', text: 'Help'},
]

const redirectTo = (path) => {
  navigate(`/${path}`)
}
</script>

<nav>
  <div class="logo" on:click={() => redirectTo('')} on:keydown="{() => {}}">
    <span class="logo-broke">Broke</span>
    <span class="logo-foodie">Foodie</span>
  </div>
  <div class="links">
    {#each links as link, index (link.name)}
      <span on:click={() => redirectTo(link.name)} on:keydown="{() => {}}" class="links-link">{link.text}</span>
    {/each}
  </div>
</nav>

<style lang="stylus">
nav
  display flex
  align-items center
  justify-content space-between
  padding 0.5rem 20rem
  width 100%
  border-radius 0.5rem

.logo
  font-size 2.5rem
  cursor pointer
  &-broke
    font-size 2rem
    font-family 'Lacquer', sans-serif
    color #34495e
    font-weight bold
  &-foodie
    font-family 'Dancing Script', sans-serif
    font-weight bold
    background -webkit-linear-gradient(bottom left,  #c0392b, #f1c40f)
    -webkit-background-clip text
    -webkit-text-fill-color transparent 

.links
  font-size 1.2rem
  display flex;
  align-items center;
  &-link
    margin-left 2rem
    cursor pointer
    transition all .2s ease-in-out
    &:hover
      color #d35400
</style>
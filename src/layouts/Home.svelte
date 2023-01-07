<script>
import { onDestroy } from 'svelte'
import { fly, fade } from 'svelte/transition'
import EatingImage from './../assets/images/eating.svg'
import { SearchOutlined } from 'svelte-ant-design-icons'
import { navigate } from 'svelte-routing'

export let query;
export let resultArray = []

const placeholderItems = ['breakfast', 'lunch', 'dinner', 'snacks', 'dessert', 'drinks']
const results = [
  {
      restaurant: 'Pruthvi Vegetarianism',
      name: 'Pav Bhaji',
      price: 100,
      service: 'Zomato'
    },
    
    {
      restaurant: 'Pruthvi Vegetarianism',
      name: 'Pav Bhaji',
      price: 130,
      service: 'Swiggy'
    }
]

let active = false

let placeholderItem =placeholderItems[0]
$: placeholder = active ? '' : `Search for ${placeholderItem}`
$: width = query ? '90%' : '100%'

const interval = setInterval(() => {
  let index = placeholderItems.indexOf(placeholderItem)
  if (index == placeholderItems.length - 1) {
    index = 0; 
  }
  else {
    index++;
  }
  placeholderItem = placeholderItems[index];
}, 1500)

const setActive = val => active =  val

onDestroy(() => {
  clearInterval(interval)
})

const search = () => {
  navigate('/search')
  console.log('this ran')
  resultArray = results
}
</script>

<div class="home" in:fade={{ delay: 200, duration: 200 }} out:fade={{ duration: 200 }}>
  <div class="home-left">
    
    <div class="home-text">
      Just enter the name of your food item <br /> and we'll search the world in order to get you the best price!
    </div>
    <div class="home-input-container">

      <input {placeholder} style:width={width} type="text" class="home-input" on:focusin={() => setActive(true)} on:focusout={() => setActive(false)} bind:value={query} />
      {#if query}
        <button on:click={search} class="home-input-button" transition:fly={{ x: 20, duration: 200 }}>
          <SearchOutlined color="#fff" />
        </button>
      {/if}
    </div>
  </div>
  <div class="home-right">
    <img src={EatingImage} alt="Man and Woman Eating">
  </div>
  </div>


<style lang="stylus">
.home
  display grid
  grid-template-columns 1fr 1fr
  position absolute
  top 40%
  left 50%
  transform translate(-50%, -50%)

  &-input
    font-size 2rem
    background #fff;
    border solid 0.2rem rgba(#eee, 1)
    transition all .2s ease-in-out
    border-radius 0.5rem
    padding 0.5rem 1rem
    &:active, &:focus
      width 90%
      border solid 0.2rem rgba(#d35400, 0.5)

    &-container
      margin-top 2rem
      display flex
      align-items center
      justify-content space-between
      width 100%


    &-button
      background -webkit-linear-gradient(bottom left,  #c0392b, #f1c40f)
      border-radius 100rem
      width 3rem
      height 3rem
      cursor pointer
      transition all .2s ease-in-out
      &:hover
        transform scale(1.1)
  
  &-text
    font-size 1.2rem

  &-left
    display flex
    flex-direction column
    aling-items flex-start
    justify-content center

  &-right
    display flex
    justify-content flex-end
    align-items center
    img
      width 90%
  

</style>
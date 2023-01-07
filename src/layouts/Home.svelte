<script>
import { onDestroy } from 'svelte'
export let query;
import EatingImage from './../assets/images/eating.svg'


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
</script>

<div class="home">
  <div class="home-left">
    
    <div class="home-text">
      Just enter the name of your food item <br /> and we'll search the world in order to get you the best price!
    </div>
    <input {placeholder} type="text" class="home-input" on:focusin={() => setActive(true)} on:focusout={() => setActive(false)} bind:value={query} />
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
    margin-top 2rem
    width 100%
    font-size 2rem
    background #fff;
    border solid 0.2rem rgba(#ccc, 1)
    transition all .2s ease-in-out
    border-radius 0.5rem
    padding 0.5rem 1rem
    &:active, &:focus
      border solid 0.2rem rgba(#d35400, 0.5)
      

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
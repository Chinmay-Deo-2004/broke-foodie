<script>

  export let name;
  export let restaurant;
  export let price;
  export let service;

</script>

<div class="result">
  <div class="result-left">
    <span class="result-restaurant">
      {restaurant}
    </span>
    <span  class="result-name">
      {name}
    </span>
    <span class="result-service">
      {service}
    </span>
  </div>
  <div class="result-right">
    <span class="result-price">₹{price}/-</span>
  </div>
</div>

<style lang="stylus">
.result
  width 100%;
  border solid 0.1rem rgba(#ccc, 1)
  bordr-radius 0.5rem
  padding 1rem 2rem
  margin-bottom 1rem
  display flex
  align-items center
  justify-content space-between

  &-price
    font-size 2rem
  &-restaurant
    font-size 1rem
  &-name
    font-size 2rem
    font-weight 500
.result-left
  display flex
  flex-direction column
</style>
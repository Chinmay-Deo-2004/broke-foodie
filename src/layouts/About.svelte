<script>
import { fade } from 'svelte/transition'

</script>

<div class="about" in:fade={{ delay: 200, duration: 200 }} out:fade={{ duration: 200 }}>
  <div class="about-text">

    <h1>Hey there, we're team BrokeFoodie</h1>
    <br/>
    <p>
      We're a group of college students who are passionate about food and
      technology. We're currently working on a project called BrokeFoodie, which
      is an app that helps you find the best food at the best price
      in your area.
    </p>
    <br />
    <p>
      We noticed that it is a hassle to check multiple apps to find the best price for your favourite food. So we decided to make an app that does that for you.
    </p>
    <br />
    <br />
    <h1>How does it work?</h1>
    <p>Since delivery websites dont' directly offer integration, we use web-scraping to get the updated prices from several food delivery websites.</p>
    <br />
    <p>Please note that we <strong>do not</strong> deliver the food, we only help you save money by comparng the prices from different delivery services. Please contact the concerned food delivery service regarding the quality, quantity and other parameters of food.</p>
    <br />
    <p>The information you get from BrokeFoodie is publicly provided by the food delivery websites, but may not always be accurate.</p>
  </div>
</div>
<style lang="stylus">
  .about
    h1
      font-size 2rem
    p
      font-size 1rem
    &-text
      width 70%
</style>
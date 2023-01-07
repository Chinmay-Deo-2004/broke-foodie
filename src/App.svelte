<script>
  import Navbar from './components/Navbar.svelte'
  import {Router, Route} from 'svelte-routing'
  import Home from './layouts/Home.svelte'
  import SearchResults from './layouts/SearchResults.svelte'
  import About from './layouts/About.svelte'
  import Docs from './layouts/Docs.svelte'

  import { fade } from 'svelte/transition'

  import './assets/stylus/common-styles.stylus'

  let query = '';

  let results = [
    
  ]

</script>


<Router url="/">
  <Navbar />
  <Route path="/">
    <Home bind:query={query} bind:results={results} />
  </Route>
  <Route path="/search">
    <SearchResults {results} bind:query={query} />
  </Route>
  <Route path="/about">
    <About />
  </Route>
  <Route path="/docs">
    <Docs />
  </Route>
</Router>

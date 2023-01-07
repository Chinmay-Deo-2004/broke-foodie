<script>
  import Navbar from './components/Navbar.svelte'
  import {Router, Route} from 'svelte-routing'
  import Home from './layouts/Home.svelte'
  import SearchResults from './layouts/SearchResults.svelte'
  import About from './layouts/About.svelte'
  import Docs from './layouts/Docs.svelte'

  import './assets/stylus/common-styles.stylus'

  let query = '';

  let results = [
    
  ]

</script>


<Router url="/">
  <Navbar />
  <Route path="/">
    <Home {query} />
  </Route>
  <Route path="/search-results">
    <SearchResults {results} {query} />
  </Route>
  <Route path="/about">
    <About />
  </Route>
  <Route path="/docs">
    <Docs />
  </Route>
</Router>

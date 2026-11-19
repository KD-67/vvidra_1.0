<script>
  import Router from 'svelte-spa-router';
  import Header from './lib/Header.svelte';
  import Footer from './lib/Footer.svelte';
  import Home from './lib/Home.svelte';
  import Navbar from './lib/Navbar.svelte';

  const routes = {
    '/': Home,
    '/navbar': Navbar
  };
</script>

<Header siteName="VVIDRA"/>

<main>
  <Router {routes} />
</main>


<Footer><p>© 2026 VVIDRA</p></Footer>
<script>
import { link } from 'svelte-spa-router'
import active from 'svelte-spa-router/active'

let { siteName } = $props();
</script>

<header>
		<nav>
			<a href="/" use:link use:active>Home</a>
			<a href="/about" use:link use:active>About</a>
		</nav>

        <h1>{siteName}</h1>
</header>

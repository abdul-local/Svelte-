<script>
	import {page,params} from './stores/pages.js';
	import router from 'page';
	import Home from './pages/Home.svelte';
	import About from './pages/About.svelte';
	import Contact from './pages/Contact.svelte';
	import Donation from './pages/Donation-now.svelte';
	import Notfound from './pages/Notfound.svelte';
	import Success from './pages/Success.svelte';
	import Failure from './pages/Failure.svelte';
	router("/",()=>($page=Home));
	router ('/sucess',()=>($page=Success));
	router('/about',()=>($page=About));
	router('/contact',()=>($page=Contact));
	router("/error",()=>($page=Failure));
	router('/donation/:id',(ctx ,next )=>{
		$params=ctx.params;
		next();
	},()=>($page=Donation));
	
	router('/*',()=>($page=Notfound));
	router.start();
	
	</script>
	<svelte:component this={$page}/>
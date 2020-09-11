
<script>
	// saya mau ambil file dari list
// import {onMount,onDestroy,beforeUpdate,afterUpdate} from 'svelte';
// inport onMoun di svelte
import {onMount} from 'svelte'
import CharityList from '../components/CharityList.svelte';
import Header from '../components/Header.svelte';
import Footer from '../components/Footer.svelte';
import Welcome from '../components/Welcome.svelte';
import Promo from '../components/Promo.svelte';
import Spiner from '../components/Spiner.svelte';

// mengambil data dari folder data
// import {charities} from '../data/charities';
// mencoba baca data dari API

let title ="Charity";
let data = getData();
async function getData(){
	const res = await fetch('https://charity-api-bwa.herokuapp.com/charities');
	 data = await res.json()
	if(data.ok){
		return data;
	}else{
		throw new Error(data);
	}
}

</script>
<Header />
<Welcome />
{#await data}
<Spiner />
{:then charities}
<CharityList {charities} />
{/await}
<Promo />
<Footer />

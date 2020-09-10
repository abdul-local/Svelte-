
<script>
	// saya mau ambil file dari list
import CharityList from '../components/CharityList.svelte';
import Header from '../components/Header.svelte';
import Footer from '../components/Footer.svelte';
import Welcome from '../components/Welcome.svelte';
import Promo from '../components/Promo.svelte';
// mengambil data dari folder data
import {charities} from '../data/charities';
let title='Opendonasi';

</script>
<Header />
<Welcome />
<CharityList {charities} />
<Promo />
<Footer />

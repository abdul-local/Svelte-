<script>
    import {onMount} from 'svelte';
    import {mapOptions } from '../config';

    let container,map;
    onMount(function(){
        map = new google.maps.Map(container,mapOptions );
        let maker = new google.maps.Maker({
            position: new google.maps.LatLng(40.6700, -73.9400),
            map,
            title:"Snazzy!",
        });
    })
</script>
<div class="xs-maps-wraper map-wraper-v2">
    <div id="xs-map" class="xs-box-shadow-2" bind:this={container} />

  </div>
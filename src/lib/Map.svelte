<script>
    import {onMount, setContext} from 'svelte'
    import {Map, View} from 'ol'
    import {Tile} from 'ol/layer'
    import {OSM} from 'ol/source'

    const minZoom = $$props['min-zoom'] ?? 1;
    const maxZoom = $$props['max-zoom'] ?? 20;
    const initialZoom = $$props['zoom'] ?? 4;

    /** @type {Map} */
    const map = new Map({
        controls: [],
        view: new View({
            zoom: initialZoom,
            center: [10383958.811375616, 8706181.502971092],
            minZoom: minZoom,
            maxZoom: maxZoom,
            projection: 'EPSG:3857'
        }),
        layers: [
            new Tile({source: new OSM()})
        ]
    })

    /** @type {HTMLDivElement} */
    let mapBox
    onMount(() => {
        map.setTarget(mapBox)
    })

    setContext('ol-svelte', {map});
</script>

<div class="map-container" bind:this={mapBox}>
    <slot/>
</div>

<style>
    .map-container {
        width: 100%;
        height: 100%;
    }
</style>

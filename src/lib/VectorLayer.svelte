<script>
    import {getContext, onMount, setContext} from 'svelte'
    import VectorLayer from 'ol/layer/Vector'
    import VectorSource from 'ol/source/Vector'

    const source = new VectorSource()
    const layer = new VectorLayer({source})

    /** @type {{map: import('ol').Map}} */
    const {map} = getContext('ol-svelte');
    onMount(() => {
        if (!map) return;
        map.addLayer(layer);

        () => layer.dispose();
    })

    setContext('ol-svelte-vector', {map, layer, source});
</script>

<slot/>

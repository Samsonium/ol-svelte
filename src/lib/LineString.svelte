<script>
    import {setContext, getContext, onMount} from 'svelte'
    import {LineString} from 'ol/geom'
    import {Feature} from 'ol'

    /** @type {[number, number][]} */
    export let coordinates = []

    const geometry = new LineString(coordinates);
    const feature = new Feature(geometry);

    /** @type {{map: import('ol').Map, layer: import('ol/layer').Vector, source: import('ol/source').Vector}} */
    const {map, layer, source} = getContext('ol-svelte-vector');
    onMount(() => {
        if (!map || !layer || !source) return;
        source.addFeature(feature);

        () => feature.dispose();
    })

    setContext('ol-svelte-linestring', {feature, geometry});
</script>

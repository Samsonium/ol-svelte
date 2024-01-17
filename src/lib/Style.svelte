<script>
    import {getContext, onMount} from 'svelte'
    import {Fill, Stroke, Style} from 'ol/style.js'

    /**
     * @type {{
     *     width: number
     *     color: string
     * }}
     */
    export let stroke

    /**
     * @type {{color: string}}
     */
    export let fill

    /** @type {{layer: import('ol/layer').Vector}} */
    const {layer} = getContext('ol-svelte-vector')
    onMount(() => {
        if (!layer) return;

        layer.setStyle(new Style({
            fill: fill ? new Fill(fill) : undefined,
            stroke: stroke ? new Stroke(stroke) : undefined
        }));
    })
</script>

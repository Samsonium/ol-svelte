<script>
    import Map from './lib/Map.svelte'
    import Style from './lib/Style.svelte'
    import LineString from './lib/LineString.svelte'
    import VectorLayer from './lib/VectorLayer.svelte'
</script>

<main>
    <Map>
        <VectorLayer>
            <LineString coordinates={[[0, 0], [1000000, 0], [1000000, 1000000], [0, 1000000], [0, 0]]} />
            <Style stroke={{width: 4, color: 'red'}} />
        </VectorLayer>
    </Map>
</main>

<style>
  main {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
  }
</style>

<script>
    import "./styles.css";
    import Clay from "$lib/Clay.svelte";
    let number = 1.0;
    let metric = false;
    $: numberInCm = metric ? number : 2.54 * number;
</script>

<svelte:head>
    <title>Pottery Calculator</title>
</svelte:head>

<div id="container">
    <div class="flex" id="main">
        <div class="row topbar">
            <div class="flex">Final Dimension</div>
            <div id="measurement" class="row">
                <button
                    class:selected={!metric}
                    on:click={() => {
                        metric = false;
                    }}>IN</button
                >
                <button
                    class:selected={metric}
                    on:click={() => {
                        metric = true;
                    }}>CM</button
                >
            </div>
        </div>
        <div>
            <input
                type="number"
                name="number"
                id="number"
                min="0"
                max="20"
                step=".125"
                bind:value={number}
            />
            <div class="slidercontainer">
                <input
                    type="range"
                    min="0"
                    max="20"
                    step=".125"
                    bind:value={number}
                    class="slider"
                    id="number-range"
                />
            </div>
        </div>
        <div id="spacer" />
    </div>

    <div class="flex">
        <Clay title="Long Beach" shrinkage={13.0} {numberInCm} />

        <Clay title="LBW" shrinkage={12.0} {numberInCm} />

        <Clay title="Soldate 60" shrinkage={13.5} {numberInCm} />

        <Clay title="B-Mix with Grog" shrinkage={10.3} {numberInCm} />

        <Clay title="Amador" shrinkage={12.0} {numberInCm} />
    </div>
</div>

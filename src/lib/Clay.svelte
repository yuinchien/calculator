<script>
    export let title;
    export let numberInCm;
    export let shrinkage;
    let showSlider = false;

    $: divide = (100 - shrinkage) / 100;
    $: sizeInInch = Math.round((numberInCm / divide / 2.54) * 100) / 100;
    $: sizeInCM = Math.round((numberInCm / divide) * 100) / 100;
</script>

<clay
    class="group"
    aria-label="clay shrinkage"
    on:mouseover={() => {
        showSlider = true;
    }}
    on:mouseout={() => {
        showSlider = false;
    }}
>
    <div class="row topbar">
        <div class="flex">{title}</div>
        <div class="slidercontainer small" aria-current={showSlider}>
            <input
                type="range"
                min="0"
                max="20"
                step=".125"
                bind:value={shrinkage}
                class="slider"
            />
        </div>
        <div class="wrapper">
            <input type="number" class="shrinkage" bind:value={shrinkage} />%
        </div>
    </div>
    <div class="row result">
        <div>{sizeInInch}</div>
        <div>{sizeInCM}</div>
    </div>
</clay>

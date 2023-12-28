<script lang="ts">
  let backgroundColor = { r: 255, g: 0, b: 0 };
  $: color = `rgb(${backgroundColor.r}, ${backgroundColor.g}, ${backgroundColor.b})`;
  console.log(color);
</script>

<main>
  <h1>Color Controller</h1>

  <div class="card">
    <div class="color-square" style="background-color: {color};"></div>
    <div>
      <input
        type="range"
        id="red"
        name="red"
        min="0"
        max="255"
        bind:value={backgroundColor.r}
        step="10"
      />
      <label for="red">Red</label>
    </div>
    <div>
      <input
        type="range"
        id="blue"
        name="blue"
        min="0"
        max="255"
        bind:value={backgroundColor.b}
        step="10"
      />
      <label for="blue">Blue</label>
    </div>
    <div>
      <input
        type="range"
        id="green"
        name="green"
        min="0"
        max="255"
        bind:value={backgroundColor.g}
        step="10"
      />
      <label for="green">Green</label>
    </div>
  </div>
</main>

<style>
  .color-square {
    width: 100px;
    height: 100px;
  }
</style>

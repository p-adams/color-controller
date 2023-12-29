<script lang="ts">
  let backgroundColor = { r: 255, g: 0, b: 0 };
  $: color = `rgb(${backgroundColor.r}, ${backgroundColor.g}, ${backgroundColor.b})`;
  $: hex = rgbToHex(backgroundColor.r, backgroundColor.g, backgroundColor.b);
  function rgbToHex(r: number, g: number, b: number): string {
    // Ensure that the values are in the valid range [0, 255]
    const clamp = (value: number) => Math.min(255, Math.max(0, value));

    // Convert each component to its hexadecimal representation
    const toHex = (value: number) => value.toString(16).padStart(2, "0");

    // Clamp and convert RGB components to hex
    const hexR = toHex(clamp(r));
    const hexG = toHex(clamp(g));
    const hexB = toHex(clamp(b));

    // Combine components to form the hex color code
    return `#${hexR}${hexG}${hexB}`;
  }
</script>

<main>
  <h1>Color Controller</h1>

  <div class="card">
    <div>
      {hex}
    </div>
    <div class="color-square" style="background-color: {color};"></div>

    <label for="red">
      <input
        type="range"
        id="red"
        name="red"
        min="0"
        max="255"
        bind:value={backgroundColor.r}
        step="10"
      />
      Red {backgroundColor.r}
    </label>

    <label for="green">
      <input
        type="range"
        id="green"
        name="green"
        min="0"
        max="255"
        bind:value={backgroundColor.g}
        step="10"
      />
      Green {backgroundColor.g}
    </label>

    <div>
      <label for="blue">
        <input
          type="range"
          id="blue"
          name="blue"
          min="0"
          max="255"
          bind:value={backgroundColor.b}
          step="10"
        />
        Blue {backgroundColor.b}
      </label>
    </div>
  </div>
</main>

<style>
  .color-square {
    width: 100px;
    height: 100px;
  }
</style>

<script lang="ts">
  import ColorControl from "./lib/ColorControl.svelte";
  import Counter from "./lib/ColorControl.svelte";

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
      <div class="hex-display">{hex}</div>
    </div>
    <div class="color-square" style="background-color: {color};"></div>
    <ColorControl
      label="Red"
      hexVal={rgbToHex(backgroundColor.r, 0, 0)}
      numberVal={backgroundColor.r}
      on:onColorChange={(e) => (backgroundColor.r = e.detail.value)}
    />
    <ColorControl
      label="Green"
      hexVal={rgbToHex(0, backgroundColor.g, 0)}
      numberVal={backgroundColor.g}
      on:onColorChange={(e) => (backgroundColor.g = e.detail.value)}
    />
    <ColorControl
      label="Blue"
      hexVal={rgbToHex(0, 0, backgroundColor.b)}
      numberVal={backgroundColor.b}
      on:onColorChange={(e) => (backgroundColor.b = e.detail.value)}
    />
  </div>
</main>

<style>
  .hex-display {
    outline: 1px solid lightgray;
    font-size: x-large;
    padding: 14px;
    border-radius: 4px;
    background: #3d3d3d;
    color: #fff;
  }
  .color-square {
    width: 100px;
    height: 100px;
    box-shadow: 10px 5px 5px lightgray;
  }
</style>

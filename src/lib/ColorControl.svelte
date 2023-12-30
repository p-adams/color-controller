<script lang="ts">
  import { createEventDispatcher } from "svelte";
  let color = "";
  export let label = "";
  export let hexVal = "";
  export let numberVal = 0;
  const dispatch = createEventDispatcher();
</script>

<div class="color-input-wrapper">
  <label for={`color-input-${label}`}>
    <input
      type="range"
      id={`color-input-${label}`}
      name={`color-input-${label}`}
      min="0"
      max="255"
      bind:value={color}
      on:input={() => dispatch("onColorChange", { value: color })}
      step="1"
    />
    {label}
    {numberVal}
  </label>
  <div class="color-sample" style="background-color: {hexVal};" />
</div>

<style>
  .color-input-wrapper {
    width: 100%;
    display: flex;
    justify-content: space-between;
    align-items: center;
    gap: 10px;
  }
  .color-input-wrapper label {
    display: flex;
  }
  .color-sample {
    width: 55px;
    height: 25px;
  }
</style>

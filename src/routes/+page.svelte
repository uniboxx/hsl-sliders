<script lang="ts">
  let hue = $state(0);
  let saturation = $state(100);
  let luminosity = $state(50);
</script>

<main>
  <h1>HSL Css Color Function</h1>
  <div
    class="hsl-square"
    style="--h: {hue};--s: {saturation}%;--l: {luminosity}%"
  ></div>
  <div class="slider-container">
    <label for="hue">hue/color </label>
    <div class="slider">
      <input
        type="range"
        min="0"
        max="360"
        bind:value={hue}
        id="hue"
        list="angles"
      />
      <datalist id="angles">
        <option value="0" label="0°"></option>
        <option value="120" label="120°"></option>
        <option value="240" label="240°"></option>
        <option value="360" label="360°"></option>
      </datalist>
    </div>
    <p class="value">{hue}</p>
  </div>
  <div class="slider-container">
    <label for="saturation">saturation </label>
    <div class="slider">
      <input
        type="range"
        min="0"
        max="100"
        bind:value={saturation}
        id="saturation"
        list="percentages"
      />
      <datalist id="percentages">
        <option value="0" label="0%"></option>
        <option value="25" label="25%"></option>
        <option value="50" label="50%"></option>
        <option value="75" label="75%"></option>
        <option value="100" label="100%"></option>
      </datalist>
    </div>
    <p class="value">{saturation}%</p>
  </div>
  <div class="slider-container">
    <label for="luminosity">luminosity/color </label>
    <div class="slider">
      <input
        type="range"
        min="0"
        max="100"
        bind:value={luminosity}
        id="luminosity"
        list="percentages"
      />
      <datalist id="percentages">
        <option value="0" label="0%"></option>
        <option value="25" label="25%"></option>
        <option value="50" label="50%"></option>
        <option value="75" label="75%"></option>
        <option value="100" label="100%"></option>
      </datalist>
    </div>
    <p class="value">{luminosity}%</p>
  </div>
</main>

<style>
  main {
    width: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }

  h1 {
    font-size: 3rem;
  }
  .hsl-square {
    width: 200px;
    height: 200px;
    background-color: hsl(var(--h), var(--s), var(--l));
    border-radius: 50%;
  }

  .slider-container {
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    align-items: top;
    gap: 2rem;

    .slider {
      display: flex;
      flex-direction: column;

      datalist {
        display: flex;
        justify-content: space-between;

        option {
          transform: translateX(0.5rem);
        }
      }
    }

    label {
      min-width: 20ch;
    }
    input {
      width: 20rem;
    }
    p.value {
      width: 4rem;
      margin: 0;
      align-self: center;
      padding: 0.5rem;
      border: 1px solid white;
    }
  }
</style>

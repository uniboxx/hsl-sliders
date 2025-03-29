<script lang="ts">
  let hue = $state(0);
  let saturation = $state(100);
  let lightness = $state(50);
</script>

<svelte:head>
<title>Hsl Sliders</title>
<meta name="description" content="Tool to select an hsl color through sliders">
</svelte:head>

<main>
  <h1>HSL Css Color Function</h1>
  <div
    class="hsl-square"
    style="--h: {hue};--s: {saturation}%;--l: {lightness}%"
  ></div>
  <div class="sliders">
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
      <label for="lightness">lightness </label>
      <div class="slider">
        <input
          type="range"
          min="0"
          max="100"
          bind:value={lightness}
          id="lightness"
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
      <p class="value">{lightness}%</p>
    </div>
  </div>
</main>

<style>
  main {
    width: 100%;
    flex: 1;
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: center;
  }

  h1 {
    font-size: 3rem;
    text-align: center;
  }
  .hsl-square {
    margin-top: 3rem;
    width: 200px;
    height: 200px;
    background-color: hsl(var(--h), var(--s), var(--l));
    border-radius: 50%;
  }

  .sliders {
    margin: 3rem 0;
    display: flex;
    width: 100%;
    padding: 0 5px;
    max-width: 30rem;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    gap: 2rem;
  }

  .slider-container {
    display: flex;
    width: 100%;
    flex-direction: column;
    justify-content: space-between;
    align-items: top;
    gap: 0.5rem;

    .slider {
      flex: 1;
      display: grid;
      grid-template-columns: repeat(3, 1fr);
      input,
      datalist {
        grid-column: 1/-1;
      }
      input {
        cursor: pointer;
      }
      datalist {
        display: flex;
        justify-content: space-between;
      }
    }

    label {
      min-width: 10ch;
      text-align: center;
    }
    input {
      max-width: 20rem;
    }
    p.value {
      width: 4rem;
      margin: 0;
      align-self: center;
      padding: 0.5rem;
      border: 1px solid white;
      text-align: center;
    }

    @media screen and (min-width: 40rem) {
      flex-direction: row;
      gap: 3rem;

      .slider {
        datalist {
          width: initial;
          padding: 0;
        }
      }

      option {
        transform: translateX(10px);
      }

      p.value {
        text-align-last: left;
        width: 7ch;
      }
    }
  }
</style>

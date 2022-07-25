<script>
  import { round } from 'supergeneric'
  let critRate = 20
  let critDamage = 120

  $: totalDamage = round(
    (1 - critRate / 100 + ((critRate / 100) * critDamage) / 100) * 100,
    2,
  )
</script>

<style type="scss">
  :root {
    --input-font-size: 3rem;
  }

  label {
    display: flex;
    flex-flow: row wrap;
    align-items: center;
    margin-bottom: 1em;
    position: relative;

    > span {
      flex: 1 100%;
    }
  }

  input {
    font-size: var(--input-font-size);
    text-align: right;
    border: none;
    border-bottom: 2px dashed #ccc;
    padding: 0;

    &:focus {
      outline: none;
    }
  }

  section {
    color: rgb(111, 180, 90);
    margin-top: 2rem;
  }

  h2 {
    font-size: calc(1.3 * var(--input-font-size));
    line-height: 1em;
    margin: 0;
    padding: 0;
    letter-spacing: -0.05em;
    font-weight: normal;

    &:after {
      content: '%';
      font-size: 0.7em;
    }
  }

  em {
    font-style: normal;
    font-size: calc(0.7 * var(--input-font-size));
    margin-bottom: -0.2em;
    user-select: none;
    cursor: pointer;
  }

  span {
    font-size: 1.2rem;
    margin-bottom: 0.2rem;
  }
</style>

<!-- MARKUP -->
<main>
  <label>
    <span>Crit Rate</span>
    <input type="text" size="3" bind:value={critRate} />
    <em>%</em>
  </label>

  <label>
    <span>Crit Damage</span>
    <input type="text" size="3" bind:value={critDamage} />
    <em>%</em>
  </label>

  <section>
    <span>Average Damage</span>
    <h2>{totalDamage}</h2>
  </section>
</main>

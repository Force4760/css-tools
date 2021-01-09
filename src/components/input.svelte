<script>
  export let value;
  export let name;
</script>

<style>
  div {
    margin: auto;
    width: 100%;
    margin-bottom: 10px;
    max-width: 700px;
  }
  label {
    display: block;
    width: 100%;
    text-align: left;
    color: #ffffff;
  }
  input {
    margin: auto;
    margin-bottom: 20px;
    width: 700px;
    height: 40px;
    max-width: 100%;
    color: #242424;
    border-radius: 5px;
    padding: 10px 10px;
    border: none;
    font-family: "Lato", sans-serif;
    font-weight: 500;
    background: #fff;
    transition: all 0.5s ease;
    display: block;
    outline: none;
    box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
      0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);
  }
  input::-webkit-outer-spin-button,
  input::-webkit-inner-spin-button {
    -webkit-appearance: none;
    margin: 0;
  }

  /* Firefox */
  input[type="text"] {
    -moz-appearance: textfield;
  }
</style>

<main>
  <div><label for={value}>{name}</label></div>

  <input type="text" bind:value name={value} class="input" />
</main>

<script>
  export let fun;
  export let text;
</script>

<style>
  .btn {
    margin-bottom: 20px;
    width: 130px;
    height: 40px;
    color: #fff;
    border-radius: 5px;
    padding: 10px 25px;
    border: none;
    font-family: "Lato", sans-serif;
    font-weight: 500;
    background: #4d194d;
    cursor: pointer;
    transition: all 0.5s ease;
    position: relative;
    display: inline-block;
    outline: none;
    box-shadow: 0 3px 1px -2px rgba(0, 0, 0, 0.2),
      0 2px 2px 0 rgba(0, 0, 0, 0.14), 0 1px 5px 0 rgba(0, 0, 0, 0.12);
  }

  .btn:hover {
    background: #351135;
    box-shadow: 0 2px 4px -1px rgba(0, 0, 0, 0.2),
      0 4px 5px 0 rgba(0, 0, 0, 0.14), 0 1px 10px 0 rgba(0, 0, 0, 0.12);
  }
</style>

<main><button on:click={fun} class="btn"><span>{text}</span></button></main>

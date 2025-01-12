<script>
  import { createEventDispatcher } from "svelte";

  let dispatch = createEventDispatcher();

  let name;
  let beltColor;
  let age;
  let skills = [];
  //   let fighting = false;
  //   let sneaking = false;
  //   let running = false;

  function handleSubmit() {

    const person = {
      id: Math.random(),
      name,
      beltColor,
      age,
      skills,
    };
  
    dispatch("addPerson", person);
  }
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />

  <input type="number" placeholder="age" bind:value={age} />
  <label for="skills">Skills:</label>

  <!-- <input type="checkbox" id="fighting" bind:checked={fighting} /> Fighting
  <br />
  <input type="checkbox" id="sneaking" bind:checked={sneaking} /> Sneaking
  <br />
  <input type="checkbox" id="running" bind:checked={running} /> Running <br /> -->

  <input type="checkbox" id="fighting" bind:group={skills} value="fighting" />
  Fighting
  <br />
  <input type="checkbox" id="sneaking" bind:group={skills} value="sneaking" />
  Sneaking
  <br />
  <input type="checkbox" id="running" bind:group={skills} value="running" />
  Running <br />

  <label for="beltcolor"> Belt Color: </label>

  <select name="" id="" bind:value={beltColor}>
    <option value="black">black</option>
    <option value="orange">orange</option>
    <option value="brown">brown</option>
    <option value="white">white</option>
  </select>

  <button>Add person</button>
</form>

<style>

</style>

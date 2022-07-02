<script>
  import { createEventDispatcher } from "svelte";
  let dispatch = createEventDispatcher();
  let name;
  let colour;
  let age;
  let skills = [];
  const handleSubmit = () => {
    const person = { name, colour, id: Math.random() };
    dispatch("addPerson", person);
  };
</script>

<form on:submit|preventDefault={handleSubmit}>
  <input type="text" placeholder="name" bind:value={name} />
  <input type="text" placeholder="colour" bind:value={colour} />
  <input type="number" placeholder="age" bind:value={age} />
  <label>Skills:</label>
  <input type="checkbox" bind:group={skills} value="isHungry" />Hungry?<br />
  <input type="checkbox" bind:group={skills} value="isSleepy" />Sleepy?<br />
  <label>Choose color:</label>
  <select bind:value={colour}>
    <option value="black">Black</option>
    <option value="red">Red</option>
    <option value="blue">Blue</option>
  </select>
  <button>Add Person</button>
</form>

<style></style>

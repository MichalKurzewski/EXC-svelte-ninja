<script>
  import Modal from "./Modal.svelte";
  import AddPersonForm from "./AddPersonForm.svelte"
  let firstName = "Wiola";
  let lastName = "Foks";
  let colour = "blue";
  let time = 0;
  let people = [
    { name: "Michal", colour: "black", id: 1 },
    { name: "Wiola", colour: "red", id: 2 },
    { name: "Danny", colour: "blue", id: 3 },
    { name: "Adam", colour: "green", id: 4 },
  ];
  let showModal = false;
  const handeShowModal = () => {
    showModal = !showModal;
  };
  const handleClick = (id) => {
    people = people.filter((person) => person.id !== id);
  };
  const handleAddPerson = (e)=>{
    const person = e.detail;
    console.log(person);
    people = [person, ...people];
    showModal=false;
  }
  $: fullName = `${firstName} ${lastName}`;
</script>

<Modal {showModal} on:click={handeShowModal}>
  <AddPersonForm on:addPerson={handleAddPerson}/>
  <h3 slot="title">add person</h3>
</Modal>

<main>
  <button on:click={() => handeShowModal()}>Show modal</button>
  <p style="color:{colour}">chosen color: {colour} by {fullName} at {time}</p>
  <input type="text" bind:value={colour} />
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="time" bind:value={time} />
  {#each people as person (person.id)}
    <div>
      <h2 style="color:{person.colour}">color</h2>
      <p>{person.name} favourite color: {person.colour}</p>
      <button on:click={() => handleClick(person.id)}>press</button>
    </div>
  {:else}
    <p>noting to display</p>
  {/each}
</main>

<style>
  main {
    text-align: center;
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  h1 {
    text-transform: uppercase;
    font-size: 4em;
    font-weight: 100;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

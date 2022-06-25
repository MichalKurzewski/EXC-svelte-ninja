<script>
  let firstName = "Wiola";
  let lastName = "Foks";
  let colour = "blue";
  let time = 0;
  let people = [
	{name: "Michal", colour:"black", id:1},
	{name: "Wiola", colour:"red", id:2},
	{name: "Danny", colour:"blue", id:3},
	{name: "Adam", colour:"green", id:4},
  ]
  
  $: fullName = `${firstName} ${lastName}`;
  $: console.log(colour);
</script>

<main>
  <p style="color:{colour}">chosen color: {colour} by {fullName} at {time}</p>
  <input type="text" bind:value={colour} />
  <input type="text" bind:value={firstName} />
  <input type="text" bind:value={lastName} />
  <input type="time" bind:value = {time}/>
  {#each people as person (person.id)}
  <div>
	<h2 style="color:{person.colour}">{person.name} favourite color: {person.colour}</h2>
  </div>
  {/each }
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

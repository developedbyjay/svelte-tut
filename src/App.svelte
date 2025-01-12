<script>
  import Modal from "./Modal.svelte";
  let showModal = false;

  const toggleModal = () => {
    showModal = !showModal;
  };

  let people = [
    {
      name: "Joshua",
      beltColor: "black",
      age: 25,
      id: 1,
    },
    {
      name: "Caleb",
      beltColor: "green",
      age: 24,
      id: 2,
    },
    {
      name: "Deborah",
      beltColor: "blue",
      age: 22,
      id: 3,
    },
  ];

  let peopleMap = new Map(people.map((person) => [person.id, person]));

  function handleClick(id) {
    peopleMap.delete(id);
    people = Array.from(peopleMap.values());
  }
</script>

<Modal
  message="Sign Up"
  isPromo={false}
  {showModal}
  on:click={toggleModal}
>


</Modal>
<main>
  <button on:click={toggleModal}>Open Modal</button>
  <div>
    {#each people as person (person.id)}
      <div>
        <h4>{person.name}</h4>
        {#if person.beltColor === "black"}
          <p>Master Nainja</p>
        {:else if person.beltColor === "green"}
          <p>Green belt</p>
        {:else}
          <p>Blue belt</p>
        {/if}
        <p>{person.age} years old, has a {person.beltColor} belt</p>
        <button on:click={() => handleClick(person.id)}>Delete</button>
      </div>
    {:else}
      <p>No people found</p>
    {/each}
  </div>
</main>

<style>
  main {
    /* text-align: center; */
    padding: 1em;
    max-width: 240px;
    margin: 0 auto;
  }

  @media (min-width: 640px) {
    main {
      max-width: none;
    }
  }
</style>

<script>
  import Modal from "./Modal.svelte";
  import AddFriendForm from "./AddFriend.svelte";

  let showModal = false;

  function toggleModal() {
    showModal = !showModal;
  }

  let people = [
    {
      name: "Joshua",
      beltColor: "black",
      age: 25,
      id: 1,
      skills: ["Coding"],
    },
    {
      name: "Caleb",
      beltColor: "green",
      age: 24,
      id: 2,
      skills: ["Reading"],
    },
    {
      name: "Deborah",
      beltColor: "blue",
      age: 22,
      id: 3,
      skills: ["Praying"],
    },
  ];

  function addPerson(e) {
    people = [e.detail, ...people];
    console.log(people);
    showModal = false;
  }

  let peopleMap = new Map(people.map((person) => [person.id, person]));

  function handleClick(id) {
    peopleMap.delete(id);
    people = Array.from(peopleMap.values());
  }
</script>

<Modal message="Sign Up" isPromo={false} {showModal} on:click={toggleModal}>
  <AddFriendForm on:addPerson={addPerson} />
</Modal>
<main>
  <button on:click={toggleModal}>Open Modal</button>
  <div>
    {#each people as person (person.id)}
      <div>
        <h4>{person.name}</h4>
        {#if person.beltColor === "black"}
          <p>Master Ninja</p>
        {:else if person.beltColor === "green"}
          <p>Green belt</p>
        {:else}
          <p>Blue belt</p>
        {/if}
        <p>{person.age} years old, has a {person.beltColor} belt</p>
        {#if person.skills}
          <p>Skills include</p>
          <ul>
            {#each person.skills as skill}
              <li>{skill}</li>
            {/each}
          </ul>
        {/if}
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

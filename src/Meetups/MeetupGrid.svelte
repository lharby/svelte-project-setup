<script>
  import MeetupItem from "./MeetupItem.svelte";
  export let meetups;
</script>

<style>
    section {
      width: 100%;
      display: grid;
      grid-template-columns: 1fr;
      grid-gap: 1rem;
    }

@media (min-width: 768px) {
  section {
    grid-template-columns: repeat(2, 1fr);
  }
}

</style>

<section class="meetups">
    {#each meetups as item}
    <MeetupItem
      title={item.title}
      subtitle={item.subtitle}
      address={item.address}
      description={item.description}
      imgURL={item.imgURL}
      email={item.contactEmail}
    />
  {/each}
  </section>
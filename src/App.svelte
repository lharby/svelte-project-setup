<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

  let title = '';
  let subtitle = '';
  let description = '';
  let address = '';
  let imgURL = '';
  let contactEmail = '';
  
  let meetups = [
    {
      id: 'm1',
      title: 'Coding bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some experts that teach you how to code',
      imgURL: 'https://media.istockphoto.com/id/1047259374/photo/programming-source-code-abstract-background.jpg?b=1&s=612x612&w=0&k=20&c=ujRPoiaJlm5U3WDWcVVa1YVlFIt6Gcjr-RstzOEPbIU=',
      address: '30 Postal Street, Linz, Austria',
      contactEmail: 'code@test.com'
    },
    {
      id: 'm2',
      title: 'Swimming lessons',
      subtitle: 'Let\'s go swimming',
      description: 'In this poolside party, we will splash around',
      imgURL: 'https://brisbanekids.com.au/wp-content/uploads/2015/03/Hampton-Swim-School-instructor-with-child-floating-on-their-back-in-the-pool.png',
      address: '32 Egg Street, Graz, Switzerland',
      contactEmail: 'code@test.com'
    }
];

function addMeetup() {
  const newMeetup = {
    id: Math.random().toString(),
    title: title,
    subtitle: subtitle,
    description: description,
    imgURL: imgURL,
    address: address,
    contactEmail: contactEmail
  }
  meetups = [newMeetup, ...meetups];
}

</script>

<style>
  .meetups {
    margin-top: 6rem;
  }
  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main class="meetups">
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      value={title}
      type={"text"}
      on:input={(event) => title = event.target.value}
    />
    <TextInput
      id="subtitle"
      label="Subtitle"
      value={subtitle}
      type={"text"}
      on:input={(event) => subtitle = event.target.value}
    />
    <TextInput
      id="description"
      label="Description"
      value={description}
      type={"text"}
      on:input={(event) => description = event.target.value}
      controlType="textarea"
      rows="3"
    />
    <TextInput
      id="address"
      label="Address"
      value={address}
      type={"text"}
      on:input={(event) => address = event.target.value}
    />
    <TextInput
      id="imgURL"
      label="Image URL"
      value={imgURL}
      type={"text"}
      on:input={(event) => imgURL = event.target.value}
    />
    <TextInput
      id="contactEmail"
      label="email"
      value={contactEmail}
      type={"email"}
      on:input={(event) => contactEmail = event.target.value}
    />
    <Button type="submit" caption="Save" />

  </form>
  <MeetupGrid {meetups} />
</main>
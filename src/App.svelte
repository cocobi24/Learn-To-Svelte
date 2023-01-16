<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";

  let title = '';
  let subtitle = '';
  let address = '';
  let email = '';
  let description = '';
  let imageUrl = '';
  let meetups = [
    {
      id: 'm1',
      title: 'Coding Bootcamp',
      subtitle: 'Learn to code in 2 hours',
      description: 'In this meetup, we will have some ecperts that teach you how to code!',
      imageUrl: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQM8zOzPYn4MZgzzWKkMzCNyBvQjk5DI5b39YaVaogXNg&s',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'code@test.com',
      isFavorite: false
    },
    {
      id: 'm2',
      title: 'Swim Together',
      subtitle: 'Let\'s go for some swimming',
      description: 'We will simply swim some rounds!',
      imageUrl: 'https://www.history.com/.image/ar_1:1%2Cc_fill%2Ccs_srgb%2Cfl_progressive%2Cq_auto:good%2Cw_1200/MTY4OTA4MzI0ODc4NjkwMDAw/christmas-tree-gettyimages-1072744106.jpg',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'swim@test.com',
      isFavorite: false
    }
  ]

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address
    };

    // meetups.push(newMeetup); // DOES NOT WORK!
    meetups = [newMeetup, ...meetups];
  }

  function toggleFavorite(event) {
    const id = event.detail;
    const updateMeetup ={ ...meetups.find(m => m.id === id) };
    updateMeetup.isFavorite = !updateMeetup.isFavorite;
    const meetupIndex = meetups.findIndex(m => m.id === id);
    const updatedMeetups = [...meetups];
    updatedMeetups[meetupIndex] = updateMeetup;
    meetups = updatedMeetups;
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>

<Header />

<main>
  <form on:submit|preventDefault="{addMeetup}">
    <TextInput 
      id="title" 
      label="Title" 
      value={title} 
      on:input="{event => (title = event.target.value)}" />
    <TextInput 
      id="subtitle" 
      label="Subtitle" 
      value={subtitle} 
      on:input="{event => (subtitle = event.target.value)}" />
    <TextInput 
      id="address" 
      label="Address" 
      value={address} 
      on:input="{event => (address = event.target.value)}" />
    <TextInput 
      id="imageUrl" 
      label="Image Url" 
      value={imageUrl} 
      on:input="{event => (imageUrl = event.target.value)}" />
    <TextInput 
      id="email" 
      label="E-Mail" 
      value={email} 
      type="email"
      on:input="{event => (email = event.target.value)}" />
    <TextInput 
      id="description" 
      label="Description" 
      controlType = "textarea"
      rows = 3
      value={description} 
      on:input="{event => (description = event.target.value)}" />

    <Button type="submit" caption="Save"></Button>
  </form>
  <MeetupGrid {meetups} on:togglefavorite="{toggleFavorite}" />
</main>
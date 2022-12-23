<script>
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";

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
      contactEmail: 'code@test.com'
    },
    {
      id: 'm2',
      title: 'Swim Together',
      subtitle: 'Let\'s go for some swimming',
      description: 'We will simply swim some rounds!',
      imageUrl: 'https://www.history.com/.image/ar_1:1%2Cc_fill%2Ccs_srgb%2Cfl_progressive%2Cq_auto:good%2Cw_1200/MTY4OTA4MzI0ODc4NjkwMDAw/christmas-tree-gettyimages-1072744106.jpg',
      address: '27th Nerd Road, 32523 New York',
      contactEmail: 'swim@test.com'
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
      type="text"
      on:input="{event => (title = event.target.value)}" />
    <TextInput 
      id="subtitle" 
      label="Subtitle" 
      value={subtitle} 
      type="text"
      on:input="{event => (subtitle = event.target.value)}" />
    <TextInput 
      id="address" 
      label="Address" 
      value={address} 
      type="text"
      on:input="{event => (address = event.target.value)}" />
    <TextInput 
      id="imageUrl" 
      label="Image Url" 
      value={imageUrl} 
      type="text"
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

    <button type="submit">Save</button>
  </form>
  <MeetupGrid {meetups} />
</main>
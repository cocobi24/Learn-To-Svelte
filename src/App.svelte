<script>
  import meetups from './Meetups/meetups-store.js';
  import Header from "./UI/Header.svelte";
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import TextInput from "./UI/TextInput.svelte";
  import Button from "./UI/Button.svelte";
  import EditMeetup from "./Meetups/EditMeetup.svelte";
  import MeetupDetail from './Meetups/MeetupDetail.svelte';

  let editMode;
  let page = 'overview';
  let pageDate = {};

  function addMeetup(event) {
    editMode = null;
  }

  function cancelEdit() {
    editMode = null;
  }

  function showdetails(event) {
    page = 'details';
    pageDate.id = event.detail;
  }

  function closeDetails() {
    page = 'overview';
    pageDate = {};
  }
</script>

<style>
  main {
    margin-top: 5rem;
  }

  .meetup-controls {
    margin: 1rem;
  }
</style>

<Header />

<main>
  {#if page === 'overview'}
    <div class="meetup-controls">
      <Button on:click={() => (editMode = 'add')}>New Meetup</Button>
    </div>
    {#if editMode === 'add'}
      <EditMeetup on:save={addMeetup} on:cancel={cancelEdit} />
    {/if}
    <MeetupGrid meetups={$meetups} on:showdetails={showdetails} />
  {:else}
  <MeetupDetail id={pageDate.id} on:close={closeDetails} />
  {/if}

</main>

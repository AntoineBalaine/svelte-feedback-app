<script lang="ts">
  import FeedbackForm from "./components/FeedbackForm.svelte";
  import FeedbackList from "./components/FeedbackList.svelte";
  import FeedbackStats from "./components/FeedbackStats.svelte";
  import { FeedbackStore } from "./components/FeedbackStores";
  let feedback = FeedbackStore;

  function deleteFeedback(e: CustomEvent<number>): void {
    feedback.update((itemsArray) =>
      itemsArray.filter((item) => item.id !== e.detail)
    );
  }
</script>

<main class="container">
  <FeedbackForm />
  <FeedbackStats />
  <FeedbackList on:delete-feedback={deleteFeedback} />
</main>

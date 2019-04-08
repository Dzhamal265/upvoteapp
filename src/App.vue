<template>
  <div id="app">
    <h2 class="title has-text-centered dividing-header">UpVote!</h2>
    <div class="section">
      <article v-for="submission in sortedSubmissions" 
      :key="submission.id"
      class="media"
      :class="{'blue-border': submission.votes >= 20}">
        <submission-component 
          :submission="submission"
          :submissions="sortedSubmissions">
        </submission-component> 
      </article>
    </div>
  </div>
</template>

<script>
import SubbmissionComponent from './components/SubbmissionComponent'
import submission from './seed'

export default {
  name: 'App',
  components: {
    'submission-component': SubbmissionComponent
  },
  data() {
    return {
      submissions: submission
    }
  },
  computed: {
    sortedSubmissions() {
      return this.submissions.slice().sort((a, b) => b.votes - a.votes);
    }
  }
}
</script>

<style>
/* Miscellaneous Styles */

.dividing-header {
  margin-top: 1em;
  margin-bottom: 2em;
}

.section {
  padding: 2rem 1.5rem;
}

.media {
  max-width: 600px;
  margin: 0 auto;
  border: 1px solid #e6e7e9;
  padding: 1em 1.5em 0.5em 1.5em;
  border-radius: 0.3em;
}

.media + .media {
  margin-top: 1.5rem;
}

.blue-border {
  border: 1px solid #3373dc !important;
}

.tag {
  font-size: 0.6rem !important;
}

.icon {
  cursor: pointer;
}

.image.is-24x24 {
  display: inline;
  position: relative;
  top: 5px;
  border-radius: 20px;
}

</style>

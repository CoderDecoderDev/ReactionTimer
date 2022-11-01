<template>
<div class="card">
  <p class="has-background-primary-light content is-large has-text-weight-medium is-family-secondary">Your reaction time is: {{ score }} ms! <br> {{ rank }}</p>
</div>
</template>

<script>
export default {
    props: ['score'],
    data() {
        return {
            rank: null
        }
    },
    mounted() {
        if (this.score < 200) {
            this.rank = "You are as fast as a bullet!"
        } else if (this.score < 300) {
            this.rank = "You are as fast as a rabbit!"
        } else if (this.score < 400) {
            this.rank = "You are as fast as a snail!"
        } else {
            this.rank = "You should definitely work on your reflexes. :)"
        }
    }
}
</script>

<style>

</style>
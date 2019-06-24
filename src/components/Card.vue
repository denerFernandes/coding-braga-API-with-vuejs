<template>
  <div class="cards">
    <div class="card" style="width: 18rem;">
      <div class="card-body">
        <h5 class="card-title">{{title}}</h5>
        <p class="card-text">{{description}}</p>
        <small>Start: {{start}} - End: {{end}}</small>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props: {
    event_id: Number,
    title: String,
    description: String,
    start: String,
    end: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>

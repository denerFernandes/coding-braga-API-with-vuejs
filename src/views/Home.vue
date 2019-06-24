<template>
  <div class="row">
      <div class="col-md-3 pb-5" v-for="(event,index) in events" :key="index" >
          <a href="#" class="remove" v-on:click="deleteEvent(event.id, index)">X</a>
          <card :event_id="event.id" :title="event.title" :description="event.description" :start="event.starts_at" :end="event.ends_at" />
      </div>
  </div>
</template>

<script>
// @ is an alias to /src
import Card from '@/components/Card.vue'
import axios from 'axios'

export default {
  name: 'home',
  components: {
    Card
  },
  data(){
    return {
      events: []
    }
  },
  mounted() {
    this.getEvents()
  },
  methods: {
    getEvents: function(){
      let self = this

      axios.get('http://localhost:8000/api/v1/events')
      .then(resp => {
        self.events = resp.data
      })
      .catch(err => console.log(err))
    },
    deleteEvent: function(event_id,index){
      let self = this
      axios.post('http://localhost:8000/api/v1/events/'+event_id,{_method: 'delete'})
      .then(resp => {
        console.log(resp.data)
        if(resp.data){
          self.events.pop(index)
        }
      })
    }
  }
}
</script>

<style scoped lang="scss">
  a{
    &.remove{
      position: absolute;
      right: 50px;
      top: 10px;
      z-index: 999;
    }
  }
</style>

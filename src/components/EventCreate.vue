<template>
    <div class="row justify-content-md-center">
        <div class="col-md-6">
            <form @submit.prevent="create">
                <div class="form-group">
                    <label for="exampleInputEmail1">Title</label>
                    <input type="text" v-model="title" class="form-control" id="exampleInputEmail1" placeholder="Enter title">
                </div>

                <div class="form-group">
                    <label for="exampleInputEmail1">Description</label>
                    <input type="text" v-model="description" class="form-control" id="exampleInputEmail1" placeholder="Enter title">
                </div>

                <div class="form-group">
                    <label for="exampleInputEmail1">Start</label>
                    <input type="date" v-model="start" class="form-control" id="exampleInputEmail1" placeholder="Enter title">
                </div>

                <div class="form-group">
                    <label for="exampleInputEmail1">End</label>
                    <input type="date" v-model="end" class="form-control" id="exampleInputEmail1" placeholder="Enter title">
                </div>
            
                <button type="submit" class="btn btn-primary">Submit</button>
            </form>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data() {
        return {
            title: '',
            description: '',
            start: '',
            end: ''
        }
    },
    methods:{
        create: function(){
            axios.post('http://localhost:8000/api/v1/events', {
                title: this.title,
                description: this.description,
                starts_at: this.start,
                ends_at: this.end
            })
            .then(resp => {
                this.$router.push("/")
            })
            .catch(err => console.log(err))
        }
    }
}
</script>

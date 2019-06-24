<template>
    <div class="row justify-content-md-center">
        <div class="col-md-6">
            <div class="alert alert-danger" v-if="msg.length > 0" role="alert">
                {{msg}}
            </div>
            <form @submit.prevent="login">
                <div class="form-group">
                    <label for="exampleInputEmail1">Email address</label>
                    <input type="email" v-model="username" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" placeholder="Enter email">
                    <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
                </div>
                <div class="form-group">
                    <label for="exampleInputPassword1">Password</label>
                    <input type="password" v-model="password" class="form-control" id="exampleInputPassword1" placeholder="Password">
                </div>
                <button type="submit" class="btn btn-primary">Submit</button>
            </form>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            username: '',
            password: '',
            msg: ''
        }
    },
    methods: {
        login: function () {
            let self = this
            let username = this.username 
            let password = this.password
            this.$store.dispatch('login', { username, password })
        .then(() => this.$router.push('/'))
        .catch( function(err){
            self.msg = err.response.data.message
        } )
        }
    }
}
</script>
<template>
    <div class="bgd">
    <Navbar />
        <br>
        <div class="container">
            <div class="row">
                <div class="col-md-4 offset-md-4 mt-3">
                    <h3>User Login</h3>
                    <b-card class="bgds">
                        <form action="#" @submit.prevent="onLogin">
                            <div class="form-group">
                                <label for="email">Email</label>
                                <input type="email" v-model="creds.email" id="email" class="form-control form-control-lg">
                            </div>

                            <div class="form-group">
                                <label for="password">Password</label>
                                <input type="password" v-model="creds.password" id="password" class="form-control form-control-lg">
                            </div>

                            <div class="form-group">
                                <button class="btn btn-primary">Login</button>
                            </div>
                        </form>
                    </b-card>
                </div>
            </div>
        </div>
    </div>
</template>


<style scoped>
    h3{
        text-align: center;
        color: rgb(255, 255, 255);
    }
    .bgd{
      background-color: #0e1e27;
      height: 765px;
    }
    .bgds{
        background-color: rgb(39, 93, 114);
        opacity: 80%;
    }
    .form-group{
        color: rgb(255, 255, 255);
    }
</style>

<script>
export default {
    data(){
        return{
            creds:{}
        }
    },
    methods:{
        async onLogin(){
            await this.$auth.loginWith('local',{data:this.creds})
            .then((res)=>{

            })
            .catch((err)=>{
                alert('Invalid credentials')
            })
        }
    }
}
</script>
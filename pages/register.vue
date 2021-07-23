<template>
    <div class="bgd">
    <Navbar />
        <br>
        <div class="container">
            <div class="row">
                <div class="col-md-4 offset-md-4 mt-3">
                    <h3>User Register</h3>
                    <b-card class="bgds">
                        <form action="#" @submit.prevent="onLogin">
                            <div class="form-group">
                                <label for="email">Email</label>
                                <input type="email" id="email" class="form-control form-control-lg">
                            </div>

                            <div class="form-group">
                                <label for="password">Password</label>
                                <input type="password" id="password" class="form-control form-control-lg">
                            </div>

                            <div class="form-group">
                                <button class="btn btn-primary">Register</button>
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
        color: rgb(250, 242, 242);
    }
    .bgd{
      background-color: #0e1e27;
      height: 765px;
    }
    .bgds{
        background-color: rgb(39, 93, 114);
        opacity: 70%;
    }
    .form-group{
        color: rgb(255, 255, 255);
    }
</style>

<script>
export default {
  auth:false
}
</script>
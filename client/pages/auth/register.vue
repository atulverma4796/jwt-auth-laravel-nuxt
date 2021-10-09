<template>
    <div class="container">
        <div class="col-md-6 offset-md-3">
            <div class="card mt-4">
                <div class="card-header">
                    <p class="mb-0">Register</p>
                </div>
                <div class="card-body">
                    <form @submit.prevent="register">
                        <div class="form-group">
                            <label>Name:</label>
                            <input type="text" v-model="form.name" name="" class="form-control" :class="{'is invalid': errors.name}" placeholder="Name" id="">
                            <div class="invalid-feedback" v-if="errors.name">
                                {{errors.name[0]}}
                            </div>
                        </div>
                         <div class="form-group">
                            <label>Email:</label>
                            <input type="email" v-model="form.email" name="" class="form-control" :class="{'is invalid': errors.email}" placeholder="Email" id="">
                             <div class="invalid-feedback" v-if="errors.email">
                                {{errors.email[0]}}
                            </div>
                        </div>
                         <div class="form-group">
                            <label>Password:</label>
                            <input type="password" v-model="form.password" name="" class="form-control" placeholder="Password" id="">
                             <div class="invalid-feedback" v-if="errors.name">
                                {{errors.password[0]}}
                            </div>
                        </div>
                          <div class="form-group">
                            <input type="submit" value="Register" class="btn btn-primary w-100" >
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
export default{    
data()
{   return {
    form:{
        name:"",
        email:"",
        password:""
    }
}

},
methods:{
    async register(){
        await this.$axios.post('/auth/register',this.form);
        this.$auth.login({data:this.form});
        this.$router.push({name:'index'});
    }
}
}
</script>
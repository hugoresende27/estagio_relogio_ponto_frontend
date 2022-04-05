<template>
  <div>
    <b-form @submit.prevent="userRegister">
      
        <b-form-group
            
            label="Name:"
            label-for="input-1">

            <b-form-input
                           v-model="form.name"
                type="text"
                placeholder="Enter Name"
                required>
            </b-form-input>

        </b-form-group>

        <b-form-group
            
            label="Email address:"
            label-for="input-1">

            <b-form-input
                           v-model="form.email"
                type="email"
                placeholder="Enter email"
                required>
            </b-form-input>

        </b-form-group>
        
        

        <b-form-group 
             
            label="Your Password:" 
            label-for="input-2">

            <b-form-input
                   type="password"
            v-model="form.password"
            placeholder="Enter Password"
            required>
            </b-form-input>

        </b-form-group>


        <b-form-group 
             
            label="Confirm Your Password:" 
            label-for="input-2">

            <b-form-input
                   type="password"
            v-model="form.password_confirmation"
            placeholder="Confirm Password"
            required>
            </b-form-input>

        </b-form-group>

        <b-button type="submit" variant="primary">Submit</b-button>

    </b-form>
  </div>
</template>

<script>
export default {
  
  auth:'guest',
  mounted(){
    this.$axios.$get('/sanctum/csrf-cookie');
  },
 


  data(){
        return{
            errors:{

            },
            form: {

                  name: "",
                  email: "",
                  password: "",
                  password_confirmation: ""
                }
                  }

    },


  methods: {
    async userRegister() {
      try {
        
        await this.$axios.post('api/register', this.form )
           await this.$auth.loginWith('laravelSanctum', { data: this.form })

            // this.$router.push('/')
        } catch (e) {
          this.error = e.response.data.message
        }
    }
  }
}

</script>
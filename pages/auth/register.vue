<template>
  <div class="my-center">
    <b-form @submit.prevent="userRegister">
      
        <b-form-group
            
            label="Name:"
            label-for="input-1">

            <b-form-input
                           v-model="form.name"
                type="text"
                placeholder="Enter Name"
                >
            </b-form-input>

            <p class="" v-if="errors.name">
                          {{ errors.name.join(" ") }}  
            </p>
             

        </b-form-group>

        <b-form-group
            
            label="Email address:"
            label-for="input-1">

            <b-form-input
                           v-model="form.email"
                type="email"
                placeholder="Enter email"
                >
            </b-form-input>

            <p class="" v-if="errors.email">
                          {{ errors.email.join(" ") }}  
            </p>
        </b-form-group>
        
        

        <b-form-group 
             
            label="Your Password:" 
            label-for="input-2">

            <b-form-input
                   type="password"
            v-model="form.password"
            placeholder="Enter Password"
            >
            </b-form-input>

            <p class="" v-if="errors.password">
                          {{ errors.password.join(" ") }}  
            </p>

        </b-form-group>


        <b-form-group 
             
            label="Confirm Your Password:" 
            label-for="input-2">

            <b-form-input
                   type="password"
            v-model="form.password_confirmation"
            placeholder="Confirm Password"
            >
            </b-form-input>

            <p class="" v-if="errors.password_confirmation">
                              {{ errors.password_confirmation.join(" ") }}
                              </p>

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
    
            form: {

                  name: "",
                  email: "",
                  password: "",
                  password_confirmation: ""
                },
            errors: ''
            
            }

    },


  methods: {
    async userRegister() {
      try {

        let errors = []
                    await this.$axios.$get('sanctum/csrf-cookie')
                    await this.$axios.$post('api/register', this.form)
                        .then((resp) => { this.$auth.loginWith('laravelSanctum', {data: this.form})})
                        .catch((err) => {
                            if (err.response.status = 422) {
                                errors = err.response.data.errors
                            }
                        })
                        this.errors = errors
        /*
        await this.$axios.post('api/register', this.form )

        await this.$auth.loginWith('laravelSanctum', { data: this.form })

         */
        } catch (err) {
          
        }
    }
  }
}

</script>
<template>
  <div class="my-center">
   <p class="">{{ errors }}</p>
    <b-form @submit.prevent="userLogin">
     
        <b-form-group
            id="input-group-1"
            label="Email address:"
            label-for="input-1">

            <b-form-input
                id="input-1"
                v-model="form.email"
                type="email"
                placeholder="Enter email"
                required>
            </b-form-input>

        </b-form-group>
        
        

        <b-form-group 
            id="input-group-2" 
            label="Your Password:" 
            label-for="input-2">

            <b-form-input
            id="input-2"
            type="password"
            v-model="form.password"
            placeholder="Enter Password"
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


  data() {
    return {
      form: {
        email: '',
        password: ''
      },
      errors: ''
    }
  },
  methods: {
    async userLogin() {
      try {
         await this.$auth.loginWith('laravelSanctum', { data: this.form })
      
      } catch (err) {

        this.errors = 'Could not sign you in with those credentials.'
        console.log(err)
      }
    }
  }
}
</script>
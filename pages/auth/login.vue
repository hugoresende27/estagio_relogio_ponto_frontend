<template>
  <div>
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
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('laravelSanctum', { data: this.form })
        // this.$auth.setUser(response.data)
        // console.log(this.$auth)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
<template>
    <div>
        <h1>Companies</h1>

        <p v-for="company in companies" :key="company.id" > {{ companies.data }} </p>


    </div>
</template>


<script>
export default {
    middleware:'auth',

    mounted(){
        this.$axios.$get('/sanctum/csrf-cookie');
        console.log(this.$auth.user)
    },

    
    async fetch(){
      this.companies = await fetch ('http://localhost:8000/api/companies').then(res=>res.json())
     
      // console.log($.parseJSON(undefined));
      //  console.log(JSON.parse(undefined));
      console.log(this.companies)

    



    },



    data(){
    return {
      content: '',
      companies: [],
    }
  },

  methods: {

        

    }
}
</script>
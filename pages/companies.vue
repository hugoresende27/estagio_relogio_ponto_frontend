<template>
    <div>
        

  	<p class="text-2xl mb-3 font-bold">Companies</p>

		<p><b>Company Name</b> : {{ companies }}</p>

    <!-- <span :for="company in companies">{{ company }} </span> -->

    </div>
</template>


<script>
export default {
    middleware:'auth',



    // mounted(){
    //         this.$axios.$get('/sanctum/csrf-cookie');
    //         console.log(this.$auth.user)
    //     },

    data() {
          return {
            companies: [],
          }
        },
    

    async fetch() {
  
          this.companies = 
                await this.$axios.$get("/api/companies/", 
                  { headers: { "X-CSRFToken": this.$axios.$get('/sanctum/csrf-cookie')} 
                });

          console.log(companies);

       
    }

    


}
</script>
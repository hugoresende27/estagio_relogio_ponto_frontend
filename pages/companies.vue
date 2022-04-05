<template>
    <div class="p-3">
        
        <h1>Companies</h1>
  
      <table class="table table-dark text-center" >
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">NIF</th>
            <th scope="col">Email</th>
            <th scope="col">Location</th>
          </tr>
        </thead>
        <tbody >
            <tr v-for="(company, index) in companies" :key="index">
                 <td> {{ company.name }}</td>
                 <td> {{ company.nif }}</td>
                 <td> {{ company.email }}</td>
                 <td> {{ company.location_id }}</td>
            </tr>
       
          
         
        </tbody>
      </table>
    

    </div>
</template>


<script>
export default {
    middleware:'auth',

    data() {
          return {
            companies: [ {
              
              
              }],

       
            }
        },

    
    

    async fetch( ) {

       
  
          this.companies = 
                await this.$axios.$get("/api/companies/").then((response)=> {
                
                    return response.data
               
                })

    },



}
</script>
<template>
    <div>
        <h1>Employees</h1>

        <!-- <p v-for="emp in employees" :key="emp.id" > {{ employees.data }} </p> -->

        <p>{{ employees}}</p>

        

    </div>
</template>


<script>
export default {
    middleware:'auth',


    data(){
        return {
            
            employees: [],
            }
    },

    // mounted(){
    //     this.$axios.$get('/sanctum/csrf-cookie');
    //     console.log(this.$auth.user)
    // },

    
    async fetch(){
    //   this.employees = await fetch ('http://localhost:8000/api/employees').then(res=>res.json())

       this.employees = 
                await this.$axios.$get("/api/employees", 
                  { headers: { "X-CSRFToken": this.$axios.$get('/sanctum/csrf-cookie')} 
                });
     
     
      console.log(this.employees)

    },






}
</script>
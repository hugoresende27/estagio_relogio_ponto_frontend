<template>
    <div class="p-3">
        <h1>Employees</h1>

        <!-- {{ employees }} -->

        <table class="table table-dark text-center" >
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">NIF</th>
            <th scope="col">NISS</th>
            <th scope="col">Start Date</th>
            <th scope="col">Email</th>
            <th scope="col">Company</th>
          </tr>
        </thead>
        <tbody >
            <tr v-for="(employee, index) in employees" :key="index">
          
                 <td> {{ employee.name }}</td>
                 <td> {{ employee.nif }}</td>
                 <td> {{ employee.niss }}</td>
                 <td> {{ employee.start_date }}</td>
                 <td> {{ employee.email }}</td>
                 <td> {{ employee.company_id }}</td>
            </tr>
       
          
         
        </tbody>
      </table>

        

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

 
    async fetch(){
   

       this.employees = await this.$axios.$get("/api/employees" ).then((response)=> {
                
                    return response.data
                 
                })
       this.employees_todos = await this.$axios.$get("/api/employees" )
       console.log(this.employees_todos)
                 
    },
    

}
</script>
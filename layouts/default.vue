  <template>

     <div class="container ">

 
        <b-navbar type="dark" variant="dark">

            <b-navbar-nav>
                
                <NuxtLink to='/' class="text-white">Relogio de Ponto</NuxtLink>

           
               

            </b-navbar-nav>

            <b-navbar-nav class="left-align">

                <div v-if="!$auth.loggedIn">
                  <NuxtLink to='/auth/login' class="btn btn-success mr-3">Login</NuxtLink>
                
                  <NuxtLink to='/auth/register' class="btn btn-success">Register</NuxtLink>           
                </div>

                <div v-if="$auth.loggedIn">

                  <button type="button" class="btn btn-danger " @click="logout">Logout</button>

                </div>
              
           

            </b-navbar-nav>

        </b-navbar>


      

      <div  class="my-side-bar p-3">
        <ul  v-if="$auth.loggedIn" class="nav flex-column">
                <li class="nav-item">
                   <NuxtLink to='/dashboard' class="text-white">Dashboard</NuxtLink>
	                
                </li>
                <li class="nav-item">
                    <NuxtLink to='/companies' class="text-white">Companies</NuxtLink>
                </li>
                <li class="nav-item">
                    <NuxtLink to='/employees' class="text-white">Employees</NuxtLink>
                </li>
                <li class="nav-item">
                     <NuxtLink to='/testes' class="text-white">TESTES</NuxtLink>
                </li>
        </ul>
      </div>
         
        

        <div class="my-main-content">
            <nuxt/>
        </div>

    </div>

  </template>


<script>
export default {

      head() {
      return {
        title: 'Relogio de Ponto',
       
      }
    },


 auth:false,

		methods:{
			async logout(){
				this.$nuxt.$loading.start();
				this.$auth.logout();
				this.$nuxt.$loading.finish();
				// this.$router.push('/login');
			}
		}
}
</script>


<style>

      .my-main-content{
        margin-left: 150px;
        background-color: grey;
        height: 80vh;
      }


      .left-align {
          margin-left: auto;
      }

      .my-side-bar{
        position: absolute;
        background-color: #000;
        width: 150px;
        height: 80vh;
        text-align: center;
      }
      .my-side-bar li{
        
        margin: 20px ;
      }

      .my-center{ 
        display: flex;          /*coloca tudo em linha*/
        flex-direction: column; /*coloca tudo em coluna*/
        align-items: center;             
        justify-content: center;/*alinha tudo verticalmente com uso de height:100vh*/
        height: 80vh;
      }


</style>
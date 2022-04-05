  <template>

     <div class="container ">

 
        <b-navbar type="dark" variant="dark">

            <b-navbar-nav>
                
                <NuxtLink to='/' class="my-title">Relogio de Ponto</NuxtLink>

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


      

      <div  class="my-side-bar">
        <ul  v-if="$auth.loggedIn" class="nav flex-column">

            <NuxtLink class="my-nav-btn mt-3 mb-3 text-white " to='/dashboard' >Dashboard </NuxtLink>


            <NuxtLink  class="my-nav-btn mb-3 text-white" to='/companies' >Companies</NuxtLink>


            <NuxtLink  class="my-nav-btn mb-3 text-white" to='/employees' >Employees</NuxtLink>


            <NuxtLink class="my-nav-btn mb-3 text-white"  to='/testes' >TESTES</NuxtLink>
                
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


      .my-title{
        color: #fff;
        font-size: 2rem;

      }

/*///////////////////BUTTONS ///////////////////////////////////*/
     @import url('https://fonts.googleapis.com/css2?family=Hind:wght@300&display=swap');

      .my-nav-btn{
        background: rgb(18,85,17);
        background: linear-gradient(105deg, rgba(18,85,17,1) 0%, rgba(19,32,4,1) 100%);
        padding: 5px;
        border-radius: 10px;
        font-size: 1.3rem;
        font-family: 'Hind', sans-serif;
        
      }

      .my-nav-btn:hover{
        background: rgb(3,39,39);
        background: linear-gradient(105deg, rgba(3,39,39,1) 0%, rgba(3,5,4,1) 97%);

      }
      .my-nav-btn a{
        color: #fff;
      }

/*/////////////////// MAIN CONTENTS ///////////////////////////////////*/
      .my-main-content{
        color:#fff;
        background: rgb(3,39,39);
        background: linear-gradient(105deg, rgba(3,39,39,1) 0%, rgba(3,5,4,1) 97%);
        margin-left: 150px;   
        height: 80vh;
      }


      .left-align {
          margin-left: auto;
      }

      .my-side-bar{
        position: absolute;
        background: rgb(253,187,45);
        background: linear-gradient(105deg, rgba(253,187,45,1) 14%, rgba(195,171,34,1) 75%);
        width: 150px;
        height: 80vh;
        text-align: center;
        
      }

      .my-center{ 
        display: flex;          /*coloca tudo em linha*/
        flex-direction: column; /*coloca tudo em coluna*/
        align-items: center;             
        justify-content: center;/*alinha tudo verticalmente com uso de height:100vh*/
        height: 80vh;
      }

      a:hover{
        text-decoration: none;
      }


</style>
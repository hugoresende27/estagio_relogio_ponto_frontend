  <template>

     <div class="container ">

 
        <b-navbar type="dark" variant="dark">

            <b-navbar-nav>
                
                <NuxtLink to='/' class="text-white">Relogio de Ponto</NuxtLink>

                <div v-if="$auth.loggedIn">
	                <NuxtLink to='/dashboard' class="text-white ml-3">Dashboard</NuxtLink>
                </div>
                <div v-if="$auth.loggedIn">
	                <NuxtLink to='/companies' class="text-white ml-3">Companies</NuxtLink>
                </div>
               

            </b-navbar-nav>

            <b-navbar-nav class="left-align">

              <div v-if="!$auth.loggedIn">
	            <NuxtLink to='/auth/login' class="btn btn-success mr-3">Login</NuxtLink>
              </div>

             <div v-if="!$auth.loggedIn">
	            <NuxtLink to='/auth/register' class="btn btn-success">Register</NuxtLink>
            
             </div>

             <div v-if="$auth.loggedIn">
	            <button type="button" class="btn btn-danger " @click="logout">Logout</button>
            
             </div>
            
            <!-- Navbar dropdowns -->
            <!-- <b-nav-item-dropdown text="Lang" right>
                <b-dropdown-item href="#">EN</b-dropdown-item>
                <b-dropdown-item href="#">ES</b-dropdown-item>
                <b-dropdown-item href="#">RU</b-dropdown-item>
                <b-dropdown-item href="#">FA</b-dropdown-item>
            </b-nav-item-dropdown> -->

            <!-- <b-nav-item-dropdown text="User" right>
                <b-dropdown-item href="#">Account</b-dropdown-item>
                <b-dropdown-item href="#">Settings</b-dropdown-item>
            </b-nav-item-dropdown> -->

            </b-navbar-nav>

        </b-navbar>

        <div>
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
        .left-align {
            margin-left: auto;
        }
</style>
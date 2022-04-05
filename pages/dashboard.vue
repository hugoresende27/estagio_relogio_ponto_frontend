<template>
	<div class=" p-5">
		<p class="text-2xl mb-3 font-bold">Dashboard</p>
		<p><b>User Name</b> : {{ $auth.user.user.name }}</p>
		<p><b>User Email</b> : {{ $auth.user.user.email }}</p>
		<p><b>User Role</b> : {{ $auth.user.user.role }}</p>
		<p><b>User NIF</b> : {{ $auth.user.user.nif }}</p>
		<p><b>User Emergency Contact</b> : {{ $auth.user.user.emer_contact }}</p>
		<p><b>User ID Card</b> : {{ $auth.user.user.bi_cc }}</p>

		<p><b>TENANT ID TESTE</b> : {{ $auth.user.user.tenant_id }}</p>
	

		
	</div>
</template>
<script>

	export default{
		middleware:'auth',

	
	}
</script>
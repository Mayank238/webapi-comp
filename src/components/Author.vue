<template>
	<div>
		<div v-if="user && user.length">
		  <button class="btn btn-link">@{{user[0].name}}</button>
	  </div>
	</div>
</template>
<script type="text/javascript">
import axios from 'axios'
  export default{
	props:['id'],
	data(){
		return{
			user: null,

		}
	},
	 mounted(){
    	axios.get('https://jsonplaceholder.typicode.com/users?id='+ this.id)
			     .then((response) => (this.user = response.data))
    },
}
</script>

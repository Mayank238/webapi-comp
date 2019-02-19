<template>
<div>
<div class="container">
<div class="card">
<div class="card-body" v-if="user && user.length">
<pre>
<center>
<p>
@{{user[0].username}}</hr>
<b>{{user[0].name}}</b></hr>
{{user[0].email}}</hr>
{{user[0].address.street}},{{user[0].address.suite}},{{user[0].address.city}},{{user[0].address.zipcode}}</hr>
{{user[0].phone}}</hr>
{{user[0].website}}</hr>
{{user[0].company.name}}
</p>
</center>
</pre>
</div>
</div>
</div>

</div>
</template>

<script>
import axios from 'axios'
export default{
props:['data1'],
data(){
return{
user: null
}
},
mounted(){
axios
.get('https://jsonplaceholder.typicode.com/users?id='+this.data1.userId)
.then(response => (this.user = response.data))
}
}
</script>

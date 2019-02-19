<template>
	<div>
     <b>{{ this.data.title}}</b>
     <div class="card-body">{{ this.data.body}}</div>

     <div class="card-body"><app-author :id="this.data.userId"></app-author></div>

     <hr>
      <div class="card-body" v-for="c in comm">
         <ul>
             <li>{{c.body}}</li>
         </ul>
      </div>

	</div>
</template>
<script type="text/javascript">
import axios from 'axios'
import Author from '@/components/Author'
	export default{
    props:['data'],
    data(){
        return{
            comm: null
        }
    },
    components:{
    	'app-author': Author
    },
    mounted () {
    	axios.get('https://jsonplaceholder.typicode.com/comments?postId='+ this.data.id)
                 .then((response) => (this.comm = response.data))
    }
	}
</script>

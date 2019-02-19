<template>
	<div>
		<div v-if="temp">
		<div class="container card text-center space" v-for='inf in info' v-if="info && info.length && seen">
			<div class="card-body" >
				<button class="btn btn-link" @click='shown(inf)'><b>{{inf.title}}</b></button>
			</div>
			<div class="card-body">{{inf.body}}</div>
			<div class="card-body">
				<button class="btn btn-link left" @click="a(inf)"><app-author :id="inf.userId">
				</app-author></button>
			</div>
		</div>
		<div v-if="!seen" class="container card text-center">
			<div class="card-body">
				<app-comm :data="data"></app-comm>
			</div>
		</div>
	  </div>
	  <div v-if="!temp">
	  	<app-user :data1="data1"></app-user>
	  </div>
	</div>
</template>
<script type="text/javascript">
import axios from 'axios'
import comments from '@/components/comments'
import author from '@/components/Author'
import User from '@/components/User'
	export default{
		data(){
			return{
				info:null,
				seen:true,
				temp:true,
				data:[],
				data1:[]
			}
		},
		created(){
			axios.get('https://jsonplaceholder.typicode.com/posts')
			     .then((response) => (this.info = response.data))
		},
		components:{
			'app-comm': comments,
			'app-author': author,
			'app-user': User
		},
		methods:{
			shown(inf){
				this.seen = !this.seen
				this.data = inf
			},
			a(inf){
				 this.temp = !this.temp
         this.data1 = inf
			}

		}

}
</script>
<style>
.space{
	margin-top: 20px;
}
.left{
	margin-left: 800px;
}
</style>

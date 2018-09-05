<template>
	<div id="app">

		<button @click="addItem">
			Add item
		</button> 

		<div>
			Tip: Click on any of the items to remove it
		</div>

		<div class="box-wrapper">
			<fade-transition group :duration="300" tag="span">
				<div class="box" 
					v-for="(item, index) in list" 
					@click="remove(index)"
					:key="item">
				</div>
			</fade-transition>
		</div>

	</div>
</template>

<script>

import FadeTransition from "@/components/FadeTransition.vue";

export default {
	name: "App",
	components: {
		FadeTransition
	},
	data() {
		return {
			show: true,
			list: [1, 2, 3, 4, 5]
		}
	},
	methods: {
		remove(index) {
			this.list.splice(index, 1);
		},
		addItem() {
			let randomIndex = Math.floor(Math.random() * this.list.length);
			this.list.splice(randomIndex, 0, Math.random());
		}
	}
}

</script>
<style lang="scss">

.box-wrapper {
	display: flex;
	flex-direction: row;
	width: 100%;
	flex-wrap: wrap;
}

.box {
	display: inline-block;
	width: 50px;
	height: 50px;
	margin-top: 20px;
	margin-right: 10px;
	background-color: rgb(108, 141, 213);
	box-shadow: rgba(108, 141, 213, 0.5) 0px 6px 20px;
	border-radius: 10px;
}

</style>
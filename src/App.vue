<template>
	<div id="app">
		<!-- <div id="nav">
			<router-link to="/">Home</router-link> |
			<router-link to="/about">About</router-link>
		</div>
		<router-view/> -->
		<ElementUi></ElementUi>
	</div>
</template>

<script>
import ElementUi from './components/ElementUi.vue';
export default {
	components: {
		ElementUi: ElementUi,
	},
}
</script>

<style>
*{
	padding: 0;
	margin: 0;
}
</style>

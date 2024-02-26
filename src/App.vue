<template>
	<div class="container"><InputField /></div>
</template>
<script setup>
import InputField from "./components/InputField.vue"
</script>

<style>
* {
	margin: 0;
	padding: 0;
	font-family: "Roboto", sans-serif;
}
.container {
	margin: auto;
	width: 947px;
	height: 672px;
	border-radius: 24px;
	box-shadow: 0 2.4rem 4.8rem rgba(0, 0, 0, 0.075);
	display: flex;
	align-items: center;
	justify-content: center;
}
.spinner {
	color: red;
	stroke: red;
	fill: red;
}
</style>

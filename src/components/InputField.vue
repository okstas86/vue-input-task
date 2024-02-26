<template>
	<div class="input-container">
		<h3 class="input-container__title">Текст перед полем ввода</h3>
		<label
			class="input-container__label"
			:class="{ 'label-active': isFocused || inputValue }"
			>Название поля</label
		>
		<div
			class="input-container__under-label"
			:class="
				inputValue.length > 1000 ? 'input-container__error-background' : ''
			"
		></div>
		<textarea
			v-model="inputValue"
			@focus="handleFocus"
			@blur="handleBlur"
			@input="handleInput"
			class="input-container__textarea"
			:class="
				inputValue.length > 1000 ? 'input-container__error-background' : ''
			"
		/>
		<div v-if="inputValue.length > 1000" class="input-container__error-message">
			Ошибка
		</div>
		<div class="input-container__loading-animation" v-if="loading">
			<img src="../assets/loading.svg" alt="loading" />
		</div>

		<div class="input-container__character-counter">
			{{ inputValue.length }}/1000
		</div>
		<button @click="clearInput" class="input-container__btn">Очистить</button>
	</div>
</template>

<script>
export default {
	data() {
		return {
			inputValue: "",
			isFocused: false,
			loading: false,
		}
	},
	methods: {
		handleFocus() {
			this.isFocused = true
			this.loading = true
		},
		handleBlur() {
			this.isFocused = false
			this.loading = false
		},
		handleInput() {},
		clearInput() {
			this.inputValue = ""
		},
	},
}
</script>

<style scoped>
.input-container {
	position: relative;
	margin: 20px;
}
.input-container__title {
	color: #303030;
	font-size: 18px;
	font-weight: 500;
}

.input-container__label {
	position: absolute;
	top: 40px;
	left: 10px;
	color: #878f97;
	transition: transform 0.3s ease-out;
	z-index: 10;
}

.input-container__under-label {
	position: absolute;
	width: 326px;
	height: 20px;
	top: 30px;
	left: 0px;
	background-color: #f0f0f0;
	z-index: 2;
}
.label-active {
	transform: translateY(-5px);
	font-size: 11px;
}

.input-container__textarea {
	width: 306px;
	height: 106px;
	padding: 20px 10px;
	margin-top: 10px;
	border-radius: 10px;
	border: none;
	background-color: #f0f0f0;
	color: #4f4f4f;
	font-size: 16px;
	font-weight: 400;
}
.input-container__textarea:focus {
	border: none;
	outline: none;
}
.input-container__error-message {
	margin: 8px 0;
	color: #d6675c;
}
.input-container__error-background {
	background-color: #fbf0ef;
}

.input-container__character-counter {
	color: #878f97;
	font-size: 14px;
	font-weight: 400px;
	margin: 8px 0 10px;
}
.input-container__btn {
	color: #00b6d0;
	border: none;
	background-color: #fff;
	font-size: 14px;
	font-weight: 400;
}

.input-container__loading-animation {
	position: absolute;
	top: 35px;
	right: 5px;
	width: 24px;
	height: 24px;
	z-index: 10;
}
</style>

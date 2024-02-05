<template>
  <div class="containerAddTasks">
	<input type="text" placeholder="Write your task...">
	<input type="button" value=">" id="Button">
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
	.containerAddTasks {
		display: flex;
		justify-content: center;
		width: 100%;
	}
	.containerAddTasks input {
		font-size: x-large;
		text-align: center;
		width: 18%;
		margin-top: 60px;
		border-radius: 5px none;
	}

	#Button {
		width: 3%;
		background-color: rgb(42, 125, 242);
		border: none;
	}
</style>
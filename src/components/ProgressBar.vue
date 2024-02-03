<template>
  <div class="containerProgress">
	<h1>Tasks</h1>
	<div class="barProgress">0%</div>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
	.containerProgress {
		display: flex;
		justify-content: center;
		align-items: center; 
		flex-direction: column;
		width: 100%;
	}

	.barProgress {
		display: flex;
		justify-content: center;
		align-items: center;
		height: 2rem;
		width: 50%;  
		border: 2px solid rgb(0, 0, 0);
	}
</style>
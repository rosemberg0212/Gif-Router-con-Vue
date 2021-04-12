<template>
	<div class="footer">
		<footer class="text-center bg-dark text-white py-2 bg-gradient">
			<h3>&copy; {{year}} - Rosemberg CG</h3>
		</footer>
	</div>
</template>

<script>
export default {
data:()=>({
	year: new Date().getFullYear(),
}),
  
}
</script>
<style>
	.footer{
		position: fixed;
		bottom: 0;
		width: 100%;
	}
</style>


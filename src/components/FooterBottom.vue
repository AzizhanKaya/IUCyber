<template>
	<footer class="main-footer-bottom">
		<p>&copy; {{ new Date().getFullYear() }} IUCyber Kulübü. Tüm hakları saklıdır.</p>
		<p>Tasarım & Geliştirme: Azizhan Kaya</p>
	</footer>
</template>

<script setup>
	// no props
</script>

<style scoped>
	.main-footer-bottom {
		text-align: center;
		padding: 2rem;
		background-color: #000;
		color: var(--text-muted-color);
		font-size: 0.9rem;
	}
</style>

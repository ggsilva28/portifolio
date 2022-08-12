<script setup lang="ts"></script>

<template>
	<footer>
		<div class="page-limit">
			<div class="item left">
				<h3>Know more about me and my work at</h3>

				<a href="https://www.linkedin.com/in/ggsilva28/">Linkedin</a>
				<a href="https://www.behance.net/ggsilva28">Behance</a>
				<a href="https://github.com/ggsilva28">Github</a>
			</div>

			<div class="item right">
				<h3>Are you interest in my work? Contact me at</h3>

				<a href="mailto: gagsilva28@gmail.com">gagsilva28@gmail.com</a>
			</div>
		</div>
	</footer>
</template>

<script lang="ts">
	export default {
		name: "Footer"
	};
</script>

<style scoped>
	footer {
		width: auto;
		height: max-content;
		padding: 120px 25px;
		background-image: url("@/assets/img/footer-1920.png");
		background-position: bottom;
		background-repeat: no-repeat;
		background-size: cover;
	}

	.page-limit {
		display: flex;
		flex-flow: row nowrap;
		align-content: center;
		justify-content: center;
	}

	.page-limit .item {
		flex: 1;
		text-align: left;
		color: var(--color-contrast);
	}

	.page-limit .item h3 {
		font-size: 26px;
		font-weight: bold;
	}

	.page-limit .item a {
		display: block;
		margin-top: 30px;
		font-size: 18px;
		color: var(--color-contrast);
		text-decoration: none;
	}

	.page-limit .item a:hover {
		text-decoration: underline;
	}

	@media (max-width: 998px) {
		footer {
			padding: 25px;
		}
		.page-limit {
			flex-flow: column nowrap;
		}

		.page-limit .item {
			margin-bottom: 35px;
		}
	}
</style>

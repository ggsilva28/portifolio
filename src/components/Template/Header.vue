<script setup lang="ts">
	import Button from "../Form/Button.vue";
	import Profile from "../Commons/Profile.vue";
</script>

<template>
	<header>
		<div class="actions">
			<div class="btn-lang"></div>
			<div class="social">
				<Button href="https://www.linkedin.com/in/ggsilva28">
					<div class="icon"><font-awesome-icon icon="fa-brands fa-linkedin" /></div>
					Linkedin</Button
				>
				<Button href="https://github.com/ggsilva28">
					<div class="icon"><font-awesome-icon icon="fa-brands fa-github" /></div>
					Github</Button
				>
			</div>
		</div>
		<div class="about-me">
			<Profile></Profile>
		</div>
	</header>
</template>

<script lang="ts">
	export default {
		name: "Header"
	};
</script>

<style scoped>
	header {
		width: 100vw;
		height: 100vh;
		background-image: url("@/assets/img/header-1920.png");
		background-position: bottom;
		background-repeat: no-repeat;
		background-size: cover;
	}

	.actions {
		display: flex;
		flex-flow: row nowrap;
		justify-content: space-between;
		align-items: center;
		padding: 35px;
	}

	.social,
	.about-me {
		display: flex;
		flex-flow: row nowrap;
		align-items: center;
		justify-content: center;
		gap: 12px;
	}

	.about-me {
		height: 70%;
	}

</style>

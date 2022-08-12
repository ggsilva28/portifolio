<template>
	<div class="profile">
		<div class="pic">
			<img src="@/assets/img/profile.jpg" alt="" />
		</div>
		<div class="desc typewriter">
			<h1><span>Welcome</span> to my Portfolio</h1>
			<h2>My Name is <span class="underline"> Gabriel </span></h2>
			<h2>I'am a <span>Front End Developer</span></h2>
		</div>
	</div>
</template>

<script lang="ts">
	export default {
		name: "Profile"
	};
</script>

<style scoped>
	@import url("https://fonts.googleapis.com/css2?family=Inconsolata:wght@200;300;400;500;600;700;800;900&display=swap");

	.profile {
		display: flex;
		flex-flow: row nowrap;
		align-items: center;
		justify-content: center;
	}

	.profile .pic {
		width: 180px;
		height: 180px;
		display: none;
	}

	.profile .pic img {
		width: 100%;
		height: 100%;
		border-radius: 20px;
		object-fit: cover;
	}

	.profile .desc {
		flex: 1;
		color: var(--color-contrast);
		font-family: "Inconsolata";
		padding: 20px;
	}

	.profile .desc span:not(.underline) {
		color: var(--color-secondary);
	}

	.profile .desc span.underline {
		position: relative;
	}

	.profile .desc span.underline::after {
		content: "";
		position: absolute;
		width: 100%;
		height: 2px;
		background-color: var(--color-contrast);
		left: -1px;
		bottom: -2px;
	}

	.profile .desc h1 {
		font-weight: 300;
		font-size: 44px;
		margin-bottom: 20px;
	}

	.profile .desc h2 {
		font-weight: 300;
		font-size: 40px;
		line-height: 130%;
		opacity: 0;
		animation: fadeInFromBottom 1s ease-in-out forwards;
		animation-delay: 2.5s;
	}

	.typewriter h1 {
		overflow: hidden; /* Ensures the content is not revealed until the animation */
		border-right: 0.3px solid transparent; /* The typwriter cursor */
		white-space: nowrap; /* Keeps the content on a single line */
		margin: 0 auto; /* Gives that scrolling effect as the typing happens */
		letter-spacing: 0.15em; /* Adjust as needed */
		animation: typing 2.5s steps(40, end), blink-caret 0.75s step-end infinite;
	}

	/* The typing effect */
	@keyframes typing {
		from {
			width: 0;
		}
		to {
			width: 100%;
			border-right: 0px solid;
		}
	}

	/* The typewriter cursor effect */
	@keyframes blink-caret {
		from,
		to {
			border-color: transparent;
		}
		50% {
			border-color: orange;
		}
	}

	@keyframes fadeInFromBottom {
		from {
			opacity: 0;
			transform: translateY(20px);
		}
		to {
			opacity: 1;
			transform: translateY(0);
		}
	}

	@media (max-width: 998px) {
		.profile .desc h1 {
			font-size: 22px;
		}

		.profile .desc h2 {
			font-size: 16px;
		}
	}
</style>

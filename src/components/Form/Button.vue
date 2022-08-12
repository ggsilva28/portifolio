<template>
	<button class="btn" v-if="!href">
		<slot></slot>
	</button>

	<a class="btn" v-else :href="href" target="_blank">
		<slot></slot>
	</a>
</template>

<script lang="ts">
	export default {
		name: "Button",
		props: {
			href: String
		}
	};
</script>

<style>
	.btn {
		position: relative;
		padding: 8px 12px;
		border-radius: 10px;
		border: none;
		background-color: var(--color-contrast);
		color: var(--color-primary);
		font-weight: bold;
		font-size: 16px;
		text-decoration: none;
		line-height: 120%;
		transition: 300ms;

		display: flex;
		flex-flow: row nowrap;
		align-items: center;
		justify-content: center;
	}

	.btn .icon {
		margin-right: 8px;
	}

	.btn:hover {
		cursor: pointer;
		transform: translateY(-5px);
	}
</style>

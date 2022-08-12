<template>
	<div class="tag" v-bind:class="{ hasCounter: count }" :size="size">
		<div v-if="count" class="count tag">{{ count }}</div>
		{{ label }}
	</div>
</template>

<script lang="ts">
	export default {
		name: "TechTag",
		props: {
			label: String,
			count: Number,
			size: String,
		}
	};
</script>

<style scoped>
	.tag {
		position: relative;
		border-radius: 10px;
		padding: 4px 12px;
		border: 1px solid var(--color-secondary);
		color: var(--color-secondary);
		background-color: var(--color-background-complement);
		text-transform: capitalize;
		font-size: 16px;
	}

	.tag.hasCounter {
		padding-left: 20px;
		margin-right: 10px;
	}

	.count {
		position: absolute;
		padding: 0px;
		width: 20px;
		height: 20px;
		top: 6px;
		left: -10px;
		font-size: 12px;
		text-align: center;
	}

	[size="small"]{
		font-size: 12px;
	}
</style>

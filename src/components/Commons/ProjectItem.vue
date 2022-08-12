<script setup lang="ts">
	import type { PropType } from "vue";
	import TechTag from "./TechTag.vue";
</script>

<template>
	<a class="item" :href="link" target="_blank">
		<div class="name">
			{{ name?.replaceAll("-", " ") }}
		</div>

		<div class="tags">
			<TechTag v-for="tag of topics" :label="tag?.label" size="small"></TechTag>
		</div>
	</a>
</template>

<script lang="ts">
	export interface ITopic {
		label: string;
		count: number;
	}

	export default {
		name: "ProjectItem",
		props: {
			name: String,
			link: String,
			topics: Object as PropType<ITopic[]>
		}
	};
</script>

<style scoped>
	.item {
		padding: 10px;
		border-radius: 10px;
		background-color: var(--color-background-complement);
        text-decoration: none;
	}
	.tags {
		display: flex;
		flex-flow: row wrap;
		justify-content: flex-start;
		align-items: center;
		gap: 12px;
	}

	.name {
		text-transform: Capitalize;
		font-size: 22px;
		font-weight: bold;
		margin-bottom: 16px;
        color: var(--color-contrast);
	}
</style>

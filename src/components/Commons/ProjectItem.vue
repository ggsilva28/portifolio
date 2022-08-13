<script setup lang="ts">
	import type { PropType } from "vue";
	import TechTag from "./TechTag.vue";
	//file system
	import { ref, computed } from "vue";
</script>

<template>
	<a class="item" :href="link" target="_blank">
		<div class="image">
			<img :src="`/images/${name}.png`" @error="getBanner" />
		</div>

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
		data() {
			return {
				image: this.getBanner(this.name)
			};
		},
		props: {
			name: String,
			link: String,
			topics: Object as PropType<ITopic[]>
		},
		methods: {
			getBanner: function (event: any) {
				if (event.target) {
					let hasNode = false;

					for (let i in this.topics) {
						let index: any = i;

						if (this.topics[index].label === "node") {
							hasNode = true;
						}
					}

					if (hasNode) {
						event.target.src = "/images/node-default.png";
					} else {
						event.target.src = "/images/default.png";
					}
				}
			}
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

	.image {
		width: calc(100% + 20px);
		height: 220px;
		transform: translateX(0px) translateY(-20px);
	}

	.image img {
		width: 100%;
		height: 100%;
		object-fit: cover;
		border-radius: 10px;
	}
</style>

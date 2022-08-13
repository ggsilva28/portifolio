<script setup lang="ts">
	import Request from "@/resources/Request.vue";
	import TechTag from "@/components/Commons/TechTag.vue";
	import ProjectItem from "../Commons/ProjectItem.vue";
</script>

<template>
	<div class="main">
		<div class="page-limit">
			<h2>Technologies used in my projects</h2>

			<div class="tech-tags-list">
				<TechTag v-for="tag of tags" :label="tag?.label" :count="tag?.count" :key="tag?.topic"></TechTag>
			</div>

			<h1>My Projects</h1>

			<div class="projects-list">
				<ProjectItem v-for="repo of repoList" :name="repo.name" :topics="repo.topics" :link="repo.link" :key="repo.name"></ProjectItem>
			</div>
		</div>
	</div>
</template>

<script lang="ts">
	const request = new Request();

	export default {
		name: "Main",
		data() {
			const data: {
				repoList: any[];
				tags: any;
			} = {
				repoList: [],
				tags: {}
			};

			return data;
		},
		created: async function () {
			const response = await request.get("https://api.github.com/users/ggsilva28/repos");

			if (response.isOk) {
				this.repoList = response.data
					.filter((repo: any) => {
						return repo.topics.length > 0;
					})
					.map((repo: any) => {
						return {
							name: repo.name,
							topics: this.addTags(repo.topics),
							link: repo.html_url,
							created_at: repo.created_at
						};
					});

				this.repoList.forEach((rep: any) => {
					Object.values(rep.topics).forEach((tag: any) => {
						if (this.tags[tag.label]) {
							this.tags[tag.label].count++;
						} else {
							this.tags[tag.label] = tag;
						}
					});
				});

				//order by count
				this.tags = Object.values(this.tags).sort((a: any, b: any) => b.count - a.count);

				this.repoList = this.repoList.sort((a: any, b: any) => {
					return new Date(b.created_at).getTime() - new Date(a.created_at).getTime();
				});
			}
		},
		methods: {
			addTags: function (topics: string[]) {
				const tags: any = {};
				topics.forEach((topic: string) => {
					const tag = tags[topic];

					if (tag) {
						tags[topic].count++;
					} else {
						tags[topic] = {
							label: topic,
							count: 1
						};
					}
				});

				return tags;
			}
		}
	};
</script>

<style scoped>
	.main {
		background-color: var(--color-background);
		background-image: url("@/assets/img/main-1920.png");
		background-repeat: no-repeat;
		background-size: contain;
		background-position: top center;
		padding: 90px 30px;

		color: var(--color-contrast);
	}

	.main h2 {
		font-size: 32px;
		margin-bottom: 24px;
	}

	.main h1 {
		font-size: 44px;
		margin-top: 64px;
		margin-bottom: 24px;
	}

	.tech-tags-list {
		display: flex;
		flex-flow: row wrap;
		justify-content: flex-start;
		align-items: center;
		gap: 12px;
	}

	.projects-list {
		display: grid;
		grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
		gap: 60px;
	}
</style>

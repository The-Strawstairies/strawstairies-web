<template>
<div class="projectLists">
		<h3 class="project-btn" v-bind:class="{ active: projFilterState === filterStates.ALL }" v-on:click="projFilter(filterStates.ALL)">All</h3>
		<h3 class="project-btn" v-bind:class="{ active: projFilterState === filterStates.ART }" v-on:click="projFilter(filterStates.ART)">Art</h3>
		<h3 class="project-btn" v-bind:class="{ active: projFilterState === filterStates.ENG }" v-on:click="projFilter(filterStates.ENG)">Engineering</h3>
		<ul class="projectlist">
						<template v-if="projFilterState === filterStates.ALL">
								<router-link
										:to="post.path"
										v-for="post in projects"
										:key="post.frontmatter.date">
										<div>
												<div class="postDisplay">{{post.frontmatter.emoji}} {{post.title}}</div>
												<p v-html="post.excerpt"></p>
										</div>
								</router-link>
						</template>
				<template v-if="projFilterState === filterStates.ART">
						<router-link
								:to="post.path"
								v-for="post in artProjects"
								:key="post.frontmatter.date">
								<div>
										<div class="postDisplay">{{post.frontmatter.emoji}} {{post.title}}</div>
										<p v-html="post.excerpt"></p>
								</div>
						</router-link>
				</template>
				<template v-if="projFilterState === filterStates.ENG">
						<router-link
								:to="post.path"
								v-for="post in engProjects"
								:key="post.frontmatter.date">
								<div>
										<div class="postDisplay">{{post.frontmatter.emoji}} {{post.title}}</div>
										<p v-html="post.excerpt"></p>
								</div>
						</router-link>
				</template>
		</ul>
</div>
</template>

<script>
import moment from "moment"	
export default {
		name: "ProjectList",
		data() {
				var filterStates = {
								ART: "art",
								ENG: "engineering",
								ALL: "all"
				};
				var projFilterState = filterStates.ALL;
				return {
						filterStates,
						projFilterState
				};
		},
		methods: {
				formatDate(date) {
						return moment(date).format("MMM Do YYYY");
				},
				projFilter(type) {
						this.projFilterState = type
				}
		},
		computed: {
				projects: function () {
						return this.$site.pages
								.filter(x => x.path.startsWith("/projects/"))
								.sort(
										(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
								);
				},
				artProjects: function () {
						return this.$site.pages
								.filter(x => x.path.startsWith("/projects/"))
						    .filter(x => x.frontmatter.type === "art")
								.sort(
										(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
								);
				},
				engProjects: function () {
						return this.$site.pages
								.filter(x => x.path.startsWith("/projects/"))
								.filter(x => x.frontmatter.type === "eng")
								.sort(
										(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
								);
				},
		}
};

</script>

<style scoped>

.project-btn {
		float: left;
		margin: 0;
		margin-right: 5px;
		margin-bottom: 10px;
		color: grey;
}
.projectlist {
		margin-top: 10px;
		clear: left;
}
.active {
		color:black;
		transition-property: color;
		transition-duration: 0.5s;
		transition-delay: 0s;
}
</style>

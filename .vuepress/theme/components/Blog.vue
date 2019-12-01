<template>
<div class="blogLists clearfix">
		<ul class="blogList">
				<router-link
						:to="post.path"
						v-for="post in posts"
						:key="post.frontmatter.date">
						<div>
								<div class="postDisplay">{{post.frontmatter.emoji}}  {{post.title}}</div>
								<p v-html="post.excerpt"></p>
								<span class="badge">{{formatDate(post.frontmatter.date)}}</span>
						</div>
				</router-link>
		</ul>
</div>
</template>

<script>
import moment from "moment"

export default {
		name: "Blog",
		methods: {
				formatDate(date) {
						return moment(date).format("MMM Do YYYY");
				}
		},
		computed: {
				posts: function () {
						return this.$site.pages
								.filter(x => x.path.startsWith("/blog/"))
								.sort(
										(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
								);
				},
		}
};

</script>

<style scoped>
.postDisplay {
		clear: left;
		float:left;
}
.blogList {
		clear: left;
}
.badge {
		display: inline-block;
		border-radius: 3px;
		padding: 0 6px;
		color: #fff;
		margin-left: 10px;
		background-color: #2aa1c0;
}
</style>


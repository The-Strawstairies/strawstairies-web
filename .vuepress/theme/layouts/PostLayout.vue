<template>
  <div>
			<Nav/>
			<div class="main">
					<router-link class="mobile-home" to="/"><h1 class="article-home" v-on:click="home">Dieter Brehm</h1></router-link>
					<article class="h-entry">
							<h2 class="pageTitle p-name">{{$page.frontmatter.title}}</h2>
							<label>
									<span class="dt-published">{{formatDate($page.frontmatter.date)}}</span>
							</label>
							<Content/>
					</article>
			</div>
			<Footer/>

  </div>
</template>

<script>
import moment from "moment";
import Nav from "@theme/components/Nav";
import Footer from "@theme/components/Footer";
export default {
		components: {
				Nav,
				Footer
		},
		name: "Layout",
		methods: {
				formatDate(date) {
						return moment(date).format("MMM Do YYYY");
				}
		}
};
</script>

<style>
@import '../styles/theme.css';
</style>
<style src="prismjs/themes/prism-tomorrow.css"></style>

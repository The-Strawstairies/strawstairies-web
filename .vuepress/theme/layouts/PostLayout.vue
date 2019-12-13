<template>
  <div>
		<img class="rotate" src="circle.png" alt="">
		<div class="main">
			<header class="header">


				<img class="home-logo" src="strawberry.png" alt="">
				<h1 id="about">The<br>Strawstairies</h1>
				<Nav />

				<img class="home-animation" src="animation.gif" alt="">
			</header>
			<article class="h-entry">
					<h2 class="pageTitle p-name">{{$page.frontmatter.title}}</h2>
					<!-- <label>
							<span class="dt-published">{{formatDate($page.frontmatter.date)}}</span>
					</label> -->
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

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
			<h1 id="blog">Blog</h1>
			<Blog />
			<Footer />
		</div>
	</div>
</template>

<script>
	import 'normalize.css'
	import Vue from 'vue'
	// internal components
	import Nav from "@theme/components/Nav";
	import Footer from "@theme/components/Footer";
	import ProjectList from "@theme/components/ProjectList";
	import Blog from "@theme/components/Blog";
	import { library } from '@fortawesome/fontawesome-svg-core'
	import { faPaperPlane, faCaretRight} from '@fortawesome/free-solid-svg-icons'
	import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
	
	library.add(faCaretRight)
	Vue.component('font-awesome-icon', FontAwesomeIcon)

	// moment js for transforming, creating, and parsing dates
	import moment from "moment"

	// poppins font
	import 'typeface-poppins'

	export default {
		components: {
			Nav,
			Footer,
			ProjectList,
			Blog
		},
		name: "Layout",
		methods: {
			formatDate(date) {
				return moment(date).format("MMM Do YYYY");
			}
		},
		computed: {
			mechanics: function () {
				return this.$site.pages
					.filter(x => x.path.startsWith("/blog/"))
					.sort(
							(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
					);
			},
		}
	};
</script>

<style>
	/* @import url('https://fonts.googleapis.com/css?family=Goudy+Bookletter+1911|Lato&display=swap'); */
	@import '../styles/theme.css';
</style>
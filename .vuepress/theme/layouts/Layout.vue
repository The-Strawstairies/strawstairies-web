<template>
	<div>
		<img class="rotate" src="/circle.png" alt="">
		<div class="main">
			<header class="header">

				<img class="home-logo" src="/strawberry.png" alt="">
				<h1 id="about">The<br>Strawstairies</h1>
				<Nav />

			</header>

			<img class="home-animation" src="/animation.gif" alt="">

			<div class="colorblock hero">
				<h2>Hello, <br>This is the <br>strawstairieey</h2>

			</div>
			<div class="colorblock mechanics">
				<h2>We're <br>building a robot, <br>
					 for you </h2>

				<a href="#"><h2>Mechanics Subsystem <font-awesome-icon class="link-icon" icon="caret-right" /></h2></a>
			</div>
			<div class="colorblock electronics">
				<h2>It’s got all you <br> need! </h2>
				<a href="#"><h2>Electrical Subsystem <font-awesome-icon class="link-icon" icon="caret-right" /></h2></a>
			</div>
			<div class="colorblock software">
				<h2>Fresh, <br>guaranteed</h2>
				<a href="#"><h2>Software Subsystem <font-awesome-icon class="link-icon" icon="caret-right" /></h2></a>
			</div>
			<!-- <p class="colorblock aboutText">We're a Principles of Engineering team at Olin College of Engineering currently making
				a stair climbing robot which is able to protect snacks and other objects during movement. It features
				cute wheel-legs (whegs), active snack balancing technology, and wireless control!</p> -->
			<!-- <img class="logo" src="/robot.png" alt="" /> -->
			<!-- <h1 id="projects">Features</h1>
			<ul>
				<li>It climbs stairs!</li>
				<li>It holds snacks and other objects!</li>
				<li>wirelessly controllable!</li>
			</ul>
			<h1 id="blog">Blog</h1>
			<Blog /> -->
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
		mounted() {
		}
	};
</script>

<style>
	/* @import url('https://fonts.googleapis.com/css?family=Goudy+Bookletter+1911|Lato&display=swap'); */
	@import '../styles/theme.css';
</style>
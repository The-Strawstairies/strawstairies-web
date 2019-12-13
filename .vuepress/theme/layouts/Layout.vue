<template>
	<div>
		<img class="rotate" src="circle.png" alt="">
		<div class="main">
			<header class="header">


				<img class="home-logo" src="strawberry.png" alt="">
				<h1 id="about">The<br>StrawStairies</h1>
				<Nav />

			<img class="home-animation" src="animation.gif" alt="">

			</header>


			<div class="colorblock hero">
				<h2>Hello, <br>This is the <br>StrawStairy</h2>
				<p class="hero-copy">The StrawStairy is a stair-climbing robot with a stabilized platform. It can climb and descend standard Olin staircases, roaming the dorms to deliver strawberries. It can be controlled over the internet through a secure, encrypted wireless control system.</p>
			</div>
			<div class="colorblock mechanics" v-bind:class="{ expand: mechexpand }">
				<h2>Engineered for <br> years of safe <br> deliveries</h2>

				<a v-on:click="mechexpand = !mechexpand"><h2>Mechanical Subsystem <font-awesome-icon class="link-icon" icon="caret-right" /></h2></a>
				<template v-if="mechexpand">
					<!-- mechanical page -->
					<Content :pageKey="mechanics[0].key"></Content>
				</template>
			</div>
			<div class="colorblock colorblock-behind mechanics"></div>
			<div class="colorblock electronics" v-bind:class="{ expand: eceexpand }">
				<h2>Power to deliver <br> across campus</h2>
				<a v-on:click="eceexpand = !eceexpand"><h2>Electrical Subsystem <font-awesome-icon class="link-icon" icon="caret-right" /></h2></a>
				<template v-if="eceexpand">
					<!-- ece page -->
					<Content :pageKey="electronics[0].key"></Content>
				</template>
			</div>
			<div class="colorblock colorblock-behind electronics"></div>
			<div class="colorblock software" v-bind:class="{ expand: softexpand }">
				<h2>Fresh wireless control, guaranteed. <br> From anywhere. </h2>
				<a v-on:click="softexpand = !softexpand"><h2>Software Subsystem <font-awesome-icon class="link-icon" icon="caret-right" /></h2></a>
				<template v-if="softexpand">
					<!-- software page -->
					<Content :pageKey="software[0].key"></Content>
				</template>
			</div>
			<div class="colorblock colorblock-behind software"></div>
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
			<div class="profiles">
				<h1 class="people-title">Team</h1>
				<div>
					<img src="caroline.jpg" alt="">
					<h1>Caroline Rausch</h1>
					<p>Olin College of Engineering, class of 2022. Caroline worked on the mechanical design of the robot in CAD as well as manufacturing and assembly of the robot.</p>
				</div>
				<div>
					<img src="david.jpg" alt="">
					<h1>David Tarazi</h1>
					<p>Olin College of Engineering, class of 2022. David worked all around with different systems in the robot, focusing on the sensor processing and software/firmware for drive and balance.</p>
				</div>
				<div>
					<img src="dieter.jpg" alt="">
					<h1>Dieter Brehm</h1>
					<p>Olin College of Engineering, class of 2022. Dieter worked on the software and firmware of the control system, and assisted heavily in website design and implementation</p>
				</div>
				<div>
					<img src="sam.jpg" alt="">
					<h1>Sam Daitzman</h1>
					<p>Olin College of Engineering, class of 2022. Sam worked on the system design (like the whegs and mechnical system modeling) and the website.</p>
				</div>
			</div>
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
		data: function () {
			return {
				mechexpand: false,
				eceexpand: false,
				softexpand: false
			}
		},
		methods: {
			formatDate(date) {
				return moment(date).format("MMM Do YYYY");
			}
		},
		computed: {
			mechanics: function () {
				return this.$site.pages
					.filter(x => x.path.startsWith("/mechanical/"))
					.sort(
							(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
					);
			},
			electronics: function () {
				return this.$site.pages
					.filter(x => x.path.startsWith("/electrical/"))
					.sort(
							(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
					);
			},
			software: function () {
				return this.$site.pages
					.filter(x => x.path.startsWith("/software/"))
					.sort(
							(a, b) => new Date(b.frontmatter.date) - new Date(a.frontmatter.date)
					);
			}
		}
	};
</script>

<style>
	/* @import url('https://fonts.googleapis.com/css?family=Goudy+Bookletter+1911|Lato&display=swap'); */
	@import '../styles/theme.css';
</style>
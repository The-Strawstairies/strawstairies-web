<template>
	<div>
		<img class="rotate" src="/circle.png" alt="">
		<div class="main">
			<img class="home-logo" src="/strawberry.png" alt="">
			<h1 id="about">The<br>Strawstairies</h1>
			<Nav />

			<img src="/animation.gif" alt="">


			<div class="colorblock mechanics">
				<p>hi</p>
			</div>
			<div class="colorblock electronics">
				<p>hi</p>
			</div>
			<div class="colorblock software">
				<p>hi</p>
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
	import Vue from 'vue'
	// internal components
	import Nav from "@theme/components/Nav";
	import Footer from "@theme/components/Footer";
	import ProjectList from "@theme/components/ProjectList";
	import Blog from "@theme/components/Blog";

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
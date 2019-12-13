<template>
<header>
		<div class="nav clearfix">
				<div class="elements">
						<router-link to="/"><h1 class="nav-link" v-on:click="home">Strawstairies</h1></router-link>
						<h1>//</h1>
						<h1 class="nav-link" v-on:click="Sprint">Sprint</h1>
						<h1>//</h1>
						<h1 class="nav-link" v-on:click="projects">Budget</h1>
						<h1>//</h1>
						<h1 class="nav-link" v-on:click="blog">Blog</h1>
				</div>
		</div>
  </header>
</template>

<script>
import Vue from 'vue'

// font awesome for social media icons
import { library } from '@fortawesome/fontawesome-svg-core'
import { faInstagram } from '@fortawesome/free-brands-svg-icons'
import { faGithub } from '@fortawesome/free-brands-svg-icons'
import { faTwitter } from '@fortawesome/free-brands-svg-icons'
import { faLinkedin } from '@fortawesome/free-brands-svg-icons'
import { faPaperPlane, faCaretRight} from '@fortawesome/free-solid-svg-icons'
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
// font awesome setup
library.add(faInstagram)
library.add(faGithub)
library.add(faTwitter)
library.add(faLinkedin)
library.add(faPaperPlane)
library.add(faCaretRight)
Vue.component('font-awesome-icon', FontAwesomeIcon)


export default {
		name: 'Nav',
		data() {
				return {};
		},
		methods: {
				scrollToNav: function(id, location) {
						var currentLocation = window.location;
						if(currentLocation.pathname == "/") {
								var element = document.getElementById(id);
								element.scrollIntoView({behavior: "smooth", block: location, inline: "nearest"});
						}
				},
				home: function (event) {
						this.scrollToNav("home", "end")
				},
				about: function (event) {
						this.scrollToNav("about", "start")

				},
				projects: function (event) {
						this.scrollToNav("projects", "start")
				},
				blog: function (event) {
						this.scrollToNav("blog", "start")
				}
		}
}
</script>

<style scoped>
.icon {
		margin-left: 0.6rem;
}
</style>

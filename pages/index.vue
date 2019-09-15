<template>
	<section class="container">
<!--		<div>-->
<!--			<img width="256" src="~/assets/img/logo.png">-->
<!--			<h1>mstodo</h1>-->
<!--			<h2>mstodo web wrapper </h2>-->
<!--			<a href="https://nuxtjs.org/" target="_blank" class="btn btn-primary">Documentation</a>-->
<!--			<a href="https://github.com/nuxt/nuxt.js" target="_blank" class="btn btn-primary">GitHub</a>-->
<!--			<a href="https://electronjs.org/" target="_blank" class="btn btn-secondary">Electron</a>-->
<!--			<a href="https://github.com/electron-userland/electron-builder" target="_blank" class="btn btn-secondary">Electron Builder</a>-->
<!--		</div>-->
		<webview
				id="mstodo"
				src="https://todo.microsoft.com/login?redirectUrl=%2Fko-kr"

		>
		</webview>

	</section>
</template>

<script>
export default {
	mounted() {
		const webview = document.querySelector('webview')
		webview.addEventListener("dom-ready", function() {


			if( !webview.src.startsWith("https://login.live.com") &&
				!webview.src.startsWith("https://todo.microsoft.com") &&
				!webview.src.startsWith("https://to-do.microsoft.com") &&
				!webview.src.startsWith("https://account.microsoft.com")  )
			{
				webview.src = "https://todo.microsoft.com/login?redirectUrl=%2Fko-kr"
			}
			console.log(webview.src);

		});	}
}
</script>

<style scoped>
.container {,
	min-height: 100vh;
	display: flex;
	justify-content: center;
	align-items: center;
	text-align: center;
}
html, body {
	width: 100%;
	height: 100%;
	margin: 0;
	padding: 0;
}

body {
	display: flex;
	justify-content: center;
	align-items: center;
}

webview{
	width:100vw;
	height:100vh;
}


</style>

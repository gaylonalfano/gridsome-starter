// src/templates/Post.vue
<template>
  <Layout>
    <div v-html="$page.post.content" />
    <vue-disqus shortname="gridsomestart" v-bind:identifier="$page.post.id"></vue-disqus>
  </Layout>
</template>

<page-query>
query ($path: String!) {
	post (path: $path) {
    id
		content
	}
}
</page-query>
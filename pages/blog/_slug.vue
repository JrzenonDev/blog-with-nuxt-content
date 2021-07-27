<template>
  <main>
    <article>
      <nuxt-content :document="article" />
      <p>Post last update: {{ formatDate(article.updatedAt) }}</p>
    </article>
    <pre>{{ article }}</pre>
  </main>
</template>

<script>

export default {
  async asyncData ({ $content, params }) {
    const article = await $content('articles', params.slug).fetch()

    return { article }
  },
  methods: {
    formatDate (date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleString('pt-BR', options)
    }
  }
}
</script>

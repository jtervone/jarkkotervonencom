<template>
  <Layout class="home">
    <div v-for="{ node } in $page.allBlogPost.edges" :key="node._id" class="article">
      <section class="header">
        <g-link :to="node.path">
          <h2 v-html="node.title"/>
        </g-link>
        <p class="description">
          <span v-html="node.date"/>
        </p>
        <g-link v-if="node.image" :to="node.path">
          <g-image :src="node.image" :alt="node.image_text" />
        </g-link>
      </section>
      <section>
        <div v-html="node.content.split('\n')[0]" />
      </section>
    </div>
    <section>
      <Pager class="pagination" :info="$page.allBlogPost.pageInfo"/>
    </section>
  </Layout>
</template>

<page-query>
  query Home ($page: Int) {
    allBlogPost (perPage: 10, page: $page) @paginate {
      pageInfo {
        totalPages
        currentPage
      }
      edges {
        node {
          id
          title
          date (format: "D.M.YYYY")
          content
          description
          image
          image_text
          path
        }
      }
    }
  }
</page-query>

<script>
import { Pager } from 'gridsome'

export default {
  components: {
    Pager
  },
  metaInfo () {
    return {
      meta: [
        {
          key: 'description',
          name: 'description',
          content: 'Jarkon blogi satunnaisia kirjoituksia koskien webbiä, koodausta, tekniikkaa sekä muita harrastuksia.'
        }
      ]
    }
  }
}
</script>

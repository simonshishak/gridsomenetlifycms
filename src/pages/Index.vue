<template>
  <Layout class="home">
    <ul>
      <li v-for="{ node } in $page.allBlogPost.edges" :key="node._id">
        <router-link :to="node.path">
          <h2 v-html="node.title"/>
        </router-link>
        <span v-html="node.date"/>
        <div v-html="node.fields.description"/>
      </li>
    </ul>
  </Layout>
</template>

<page-query>
  query Home ($page: Int) {
    allBlogPost (page: $page) {
      edges {
        node {
          _id
          title
          date (format: "D MMMM, YYYY")
          fields {
            description
          }
          path
        }
      }
    }
  }
</page-query>

<style scoped>
  .home >>> .heading {
    margin-bottom: 1vh;
  }

  ul {
    list-style: none;
    padding: 0;
  }

  ul li {
    margin-bottom: 1vh;
  }

  ul li a h2 {
    margin-bottom: 1vh;
  }

  span {
    font-size: 100%;
    padding: 1vh;
  }

  ul li p:first-child {
    margin-top: 1vh;
  }

  ul li p {
    margin: 0;
    line-height: 0;
  }
</style>
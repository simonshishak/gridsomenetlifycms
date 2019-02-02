<template>
  <Layout>
    <div class="article">
      <h1>{{ $page.blogPost.title }}</h1>
      <span>{{ $page.blogPost.date }}</span>
      <img :src="$page.blogPost.fields.image"/>
      <div class="content" v-html="$page.blogPost.content" />
    </div>
  </Layout>
</template>

<script>
export default {
  metaInfo () {
    return {
      title: this.$page.blogPost.title
    }
  }
}
</script>

<page-query>
  query BlogPost ($path: String!) {
    blogPost (path: $path) {
      title
      date (format: "D MMMM, YYYY")
      content
      fields {
        image
      }
    }
  }
</page-query>

<style>
  .article {
    margin-top: 1vh;
  }

  .article h1 {
    font-size: 32px;
  }

  .article img {
    width: 100%;
    border-radius: 8px;
  }

  .article a {
    color: #4dba87;
    text-decoration: underline;
  }

  .article a:hover {
    text-decoration: none;
  }

  .article span {
    font-size: 100%;
    margin-bottom: 1vh;
  }

  .article ol, .article ul {
    list-style-position: outside;
  }

  .article ul {
    list-style: disc;
    padding-left: 1vw;
  }

  .article .content p:first-child {
    margin-top: 1vh;
  }

  .article .content p {
    margin-top: 0;
    margin-bottom: 1vh;
    line-height: 1;
  }
</style>

<template>
  <div class="layout">
    <header class="header">
      <g-link class="heading-link" :to="{ name: 'home' }">
        <component :is="titleTag" class="heading">{{ config.siteName }}</component>
      </g-link>
    </header>
    <slot/>
  </div>
</template>

<script>
import config from '~/.temp/config.js';

export default {
  computed: {
    titleTag () {
      return this.$route.name === 'home' ? 'h1' : 'h6'
    },
    config () {
      return config
    }
  }
}
</script>


<style lang="css">
  * {
    margin: 0;
    padding: 0;
  }

  a {
    color: #4dba87;
    text-decoration: none;
  }

  h1, h2, h3, h4, h5, h6 {
    font-family: 'Helvetica';
  }

  h1 {
    font-size: 32px;
  }

  h6 {
    font-size: 24px;
  }

  body {
    font-family: 'Helvetica';
    margin: 0;
    font-size: 16px;
    padding: 0;
  }

  .heading-link {
    color: black;
    text-decoration: none;
  }

  .layout {
    max-width: 25vw;
    margin: 0 auto;
    padding-left: 10vw;
    padding-right: 10vw;
  }

  .layout {
    margin-top: 10vh;
    margin-bottom: 10vh;
  }

  .heading {
    margin-bottom: 10vh;
    font-family: 'Helvetica';
    font-weight: bold;
  }
</style>

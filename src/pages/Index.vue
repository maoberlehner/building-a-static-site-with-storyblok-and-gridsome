<template>
  <Layout>
    <div class="Home">
      <div class="Home__hero mb-4 mb-md-5 mx-auto text-center">
        <h1 class="display-4">
          {{ $page.landingPage.title }}
        </h1>
        <p class="lead">
          {{ $page.landingPage.intro }}
        </p>
      </div>

      <div class="Home__media-blocks mb-5">
        <AppMediaBlock
          v-for="mediaBlock in $page.landingPage.mediaBlocks"
          :key="mediaBlock._uid"
          v-bind="mediaBlock"
        />
      </div>

      <ul class="Home__teasers mb-5">
        <li
          v-for="teaser in $page.landingPage.teasers"
          :key="teaser._uid"
        >
          <AppTeaser v-bind="teaser"/>
        </li>
      </ul>
    </div>
  </Layout>
</template>

<page-query>
query LandingPage {
  landingPage(path: "home") {
    title
    intro
    mediaBlocks {
      image
      image_position
      text
      title
    }
    teasers {
      image
      link {
        url
      }
      text
      title
    }
  }
}
</page-query>

<script>
import AppMediaBlock from '../components/AppMediaBlock.vue';
import AppTeaser from '../components/AppTeaser.vue';

export default {
  components: {
    AppMediaBlock,
    AppTeaser,
  },
};
</script>

<style>
.Home__hero {
  max-width: 36em;
}

.Home__media-blocks > :not(:last-child) {
  margin-bottom: 4em;
}

.Home__teasers {
  display: flex;
  margin-top: -1em;
  margin-left: -1em;
  padding-left: 0;
  flex-wrap: wrap;
  list-style-type: none;
}

.Home__teasers > * {
  padding-top: 1em;
  padding-left: 1em;
  flex-basis: 16em;
  flex-grow: 9999;
}
</style>

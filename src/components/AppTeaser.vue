<template>
  <div class="AppTeaser card">
    <img
      :src="imageSrc"
      :srcset="imageSrcset"
      class="card-img-top"
    >
    <div class="card-body">
      <h5 class="card-title">{{ title }}</h5>
      <p class="card-text">{{ text }}</p>
      <a
        :href="link.url"
        class="btn btn-primary"
      >
        Read more
      </a>
    </div>
  </div>
</template>

<script>
export default {
  name: `AppTeaser`,
  props: {
    image: {
      type: Object,
      default: null,
    },
    link: {
      type: Object,
      default: ``,
    },
    text: {
      type: String,
      required: true,
    },
    title: {
      type: String,
      required: true,
    },
  },
  computed: {
    imageSrc() {
      if (!this.image) return null;
      return this.image.src.replace(`a.storyblok.com`, `img2.storyblok.com/256x160`);
    },
    imageSrcset() {
      if (!this.image) return null;
      return `${this.image.src.replace(`a.storyblok.com`, `img2.storyblok.com/512x320/filters:quality(40)`)} 2x`;
    },
  },
};
</script>

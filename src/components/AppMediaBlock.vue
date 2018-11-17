<template>
  <div class="AppMediaBlock">
    <div class="AppMediaBlock__body">
      <h2>{{ title }}</h2>
      <p>{{ text }}</p>
    </div>
    <div
      v-if="image"
      :class="{
        [`AppMediaBlock__figure`]: true,
        [`AppMediaBlock__figure--left`]: image_position === `left`,
      }"
    >
      <img
        :src="imageSrc"
        :srcset="imageSrcset"
      >
    </div>
  </div>
</template>

<script>
export default {
  name: `AppMediaBlock`,
  props: {
    image: {
      type: Object,
      default: null,
    },
    image_position: {
      type: String,
      default: null,
    },
    position: {
      type: String,
      default: `right`,
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
      return this.image.src.replace(`a.storyblok.com`, `img2.storyblok.com/360x250`);
    },
    imageSrcset() {
      if (!this.image) return null;
      return `${this.image.src.replace(`a.storyblok.com`, `img2.storyblok.com/720x500/filters:quality(40)`)} 2x`;
    },
  },
};
</script>

<style>
.AppMediaBlock {
  display: flex;
  margin-top: -1em;
  margin-left: -2em;
  flex-wrap: wrap;
  align-items: center;
}

.AppMediaBlock__body,
.AppMediaBlock__figure {
  padding-top: 1em;
  padding-left: 2em;
}

.AppMediaBlock__body {
  flex-basis: 24em;
  flex-grow: 9999;
}

.AppMediaBlock__figure {
  flex-basis: 18em;
  flex-grow: 1;
  text-align: center;
}

.AppMediaBlock__figure--left {
  order: -1;
}
</style>

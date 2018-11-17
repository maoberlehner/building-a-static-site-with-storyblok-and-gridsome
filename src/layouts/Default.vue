<template>
  <div class="LayoutDefault">
    <div class="d-flex align-items-center p-3 mb-3 mb-md-5 bg-white border-bottom box-shadow">
      <span class="mr-auto">Fancy Company</span>
      <nav class="ml-auto">
        <g-link
          :to="{ name: 'home' }"
          class="p-2 text-dark">
          Home
        </g-link> |
        <g-link
          :to="{ name: 'about' }"
          class="p-2 text-dark">
          About
        </g-link>
      </nav>
    </div>
    <div class="LayoutDefault__main mx-auto">
      <slot/>
    </div>
    <footer class="d-flex align-items-center p-3 bg-white border-top box-shadow">
      &copy; Fancy Company
    </footer>
  </div>
</template>

<script>
export default {
  name: `LayoutDefault`,
  metaInfo: {
    link: [
      {
        rel: 'stylesheet',
        href: 'https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css' },
    ],
  },
};
</script>

<style>
.LayoutDefault__main {
  padding-right: 1em;
  padding-left: 1em;
  max-width: 52em;
}
</style>

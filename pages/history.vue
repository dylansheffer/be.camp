<template>
  <div
    v-if="page"
    class="page-wrapper"
  >
    <page-hero
      :background="page.hero_image"
      :accent-color="page.page_accent_color"
    >
      <h1 class="page-title">
        {{ page.page_title }}
      </h1>
      <div class="page-description">
        {{ page.page_description }}
      </div>
    </page-hero>

    <section class="page-section">
      <div class="wysiwyg-block">
        <div v-html="page.page_content"></div>
      </div>
    </section>
  </div>
</template>

<script>
import {mapState} from 'vuex'

export default {
  middleware: 'beswarm',
  head () {
    return {
      title: 'History | beCamp',
      meta: [
        { hid: 'description', name: 'description', content: 'beCamp is an implementation of barCamp, an anttendee planned unconference. Here\'s the story of how it came to be.' }
      ]
    }
  },
  created () {
    this.$store.commit('setCurrentPageAccentColor', this.page.page_accent_color)
  },
  computed: {
    ...mapState({
      butterPages: state => state.butterPages,
    }),
    page () {
      return this.butterPages['history'] ? this.butterPages['history'] : {}
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

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
  head () {
    return {
      title: 'FAQs | beCamp',
      meta: [
        { hid: 'description', name: 'description', content: 'Everything you wanted to know about beCamp, but were maybe too afraid to ask.' }
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
      return this.butterPages['faqs'] ? this.butterPages['faqs'] : {}
    }
  }
}
</script>

<style lang="scss" scoped>

</style>

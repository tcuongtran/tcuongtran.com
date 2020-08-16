<template>
  <main class="page">
    <!-- <slot name="top" /> -->
    <div class="theme-default-content"> 
        <h3 v-if="$frontmatter.type === 'posts'">{{$title}}</h3>

        <Content />
    </div>
    <PageEdit />

    <PageNav v-bind="{ sidebarItems }" />

    <!-- <slot name="bottom" /> -->
  </main>
</template>

<script>
import PageEdit from '@theme/components/PageEdit.vue'
import PageNav from '@theme/components/PageNav.vue'
export default {
  components: { PageEdit, PageNav },
  props: ['sidebarItems'],
  mounted () {
      console.log(this);
  }
}
</script>

<style lang="stylus">
.page
  padding-bottom 2rem
  display block
</style>
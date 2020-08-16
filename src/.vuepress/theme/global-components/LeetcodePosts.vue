<template>
    <div class="post-container">
        <div class="post-card" v-for="page in pages">
            <router-link :to="page.path">
                <div class="page-title">{{ page.title }}</div>
            </router-link>
            <div class="page-detail">
                <div v-html="page.excerpt"></div>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    data () {
        return {
            pages: []
        }
    },
    mounted() {
        this.pages = this.$site.pages.filter(x => x.frontmatter.tag === 'leetcode').sort((a, b) => {
            return new Date(b.frontmatter.published).getTime() - new Date(a.frontmatter.published).getTime();
        });
    }
}
</script>

<style lang="stylus" scoped>
.page-title {
    font-size: 25px;
}
</style>
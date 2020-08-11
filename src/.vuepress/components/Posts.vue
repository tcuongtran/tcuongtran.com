<template>
    <div class="post-container">
        <router-link v-for="page in pages" :to="page.path">
            <div class="post-card">
                <div class="page-detail">
                    <div class="page-title">{{ page.title }}</div>
                    <div class="page-description">{{ page.frontmatter.description }}</div>
                    <div class="page-author">Author: {{ page.frontmatter.author }}</div>
                </div>
            </div>
        </router-link>
    </div>
</template>
<script>
export default {
    data() {
        return {
            pages: []
        }
    },
    mounted() {
        this.$site.pages.forEach(page => {
            if (page.frontmatter.type === 'article') {
                this.pages.push(page)
            }
        })
    }
}
</script>
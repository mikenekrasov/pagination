<template>
  <div>
    <post-item v-for="(post, i) in posts" :key="i" :post="post"/>
    <post-pagination
      :start="start"
      :totalPages="totalPages"
      :allPosts="returnPosts"
      @next="nextPage"
      @prev="prevPage"
      @page="currentPage"
    >
    </post-pagination>
  </div>
</template>

<script>
  import PostItem from '~/components/postItem'
  import PostPagination from '~/components/PostPagination'

  export default {
    name: 'PostsList',
    components: {
      PostItem,
      PostPagination
    },
    data: () => ({
      posts: [],
      page: 1,
      start: 0,
      postsPerPage: 10,
      totalPages: 10,
      allPosts: null
    }),
    created() {
      if (this.$route.query.page) {
        this.page = parseInt(this.$route.query.page)
        this.start = parseInt(this.page + '0') - 10
      }
      this.getPosts()

    },
    mounted() {
    },
    computed: {
      returnPosts() {
        return this.totalPages * this.postsPerPage
      }
    },
    methods: {
      nextPage() {
        this.start = this.start + 10
        this.page = this.page + 1
        this.$router.push({ query: { page: this.page } })
        this.getPosts()
      },
      prevPage() {
        this.start = this.start - 10
        this.page = this.page - 1
        this.$router.push({ query: { page: this.page } })
        this.getPosts()
      },
      currentPage(page) {
        this.page = page
        this.start = parseInt(this.page + '0') - 10
        this.$router.push({ query: { page: this.page } })
        this.getPosts()
      },
      async getPosts() {
        try {
          this.posts = await this.$axios.$get(`https://jsonplaceholder.typicode.com/posts?_start=${this.start}&_limit=${this.postsPerPage}`)
          // this.$axios.$get(`https://jsonplaceholder.typicode.com/posts?page=${this.page}&_start=${this.start}&_limit=${this.perPage}`)
        } catch (e) {
          console.log(e)
        }


      }
    }
  }
</script>

<style scoped>
</style>

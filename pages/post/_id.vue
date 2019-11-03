<template>
  <article class="post-single">
    <div class="container post-single__container">
      <h1 class="post-single__title">{{ post.title }}</h1>
      <div class="post-single__content">
        {{ post.body }}
      </div>
      <ul class="post-single__comments comments__list">
        <postComment
          v-for="comment in comments"
          :key="comment.id"
          :comment="comment"
        >
        </postComment>
      </ul>
      <button
        v-if="this.comments.length !== totalComments"
        @click="showMore"
        :disabled="loading"
        class="post-single__load-more"
      >
        Показать ещё
      </button>
    </div>
  </article>
</template>

<script>
  import PostComment from '~/components/PostComment'

  export default {
    components: {
      PostComment
    },
    data: () => ({
      post: {},
      comments: [],
      commentsPerPage: 2,
      page: 1,
      totalComments: 5, // x-total-count
      loading: false
    }),
    created() {
      this.getPosts()
      this.getComments()
    },
    methods: {
      async getPosts() {
        try {
          this.post = await this.$axios.$get(`https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`)
        } catch (e) {
          console.log(e)
        }
      },
      async getComments() {
        try {
          this.comments = await this.$axios.$get(`https://jsonplaceholder.typicode.com/comments?postId=${this.$route.params.id}&_limit=${this.commentsPerPage}`)
        } catch (e) {
          console.log(e)
        }
      },
      async showMore() {
        this.loading = true
        try {
          this.page++
          let newComments = await this.$axios.$get(`https://jsonplaceholder.typicode.com/comments?postId=${this.$route.params.id}&_page=${this.page}&_limit=${this.commentsPerPage}`)
          this.comments = [...newComments, ...this.comments]
          this.loading = false
        } catch (e) {
          console.log(e)
        }

      }
    }
  }
</script>
<style lang="scss">
  .container {
    margin: 0 auto;
    width: 970px;
  }

  .post-single {
    margin-top: 60px;

    &__title {
      font-family: "Open Sans", sans-serif;
      font-weight: bold;
      font-size: 45px;
      line-height: 50px;
    }

    &__content {
      margin-top: 46px;
      margin-bottom: 60px;
    }

    &__load-more {
      font-size: 13px;
      line-height: 25px;
      padding: 8px 51px;
      background: transparent;
      border: none;
      display: flex;
      align-items: center;
      margin: 0 auto;
      cursor: pointer;

      &:before {
        content: '';
        width: 12px;
        height: 12px;
        background: url("~assets/more.png");
        margin-right: 8px;
        display: inline-block;
      }
    }
  }

  .comments__list {
    padding-left: 0;
    list-style: none;
    margin-bottom: 80px;
  }

</style>

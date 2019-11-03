<template>
  <div class="post-pagination">
    <div v-if="start !== 0" @click="firstPage" class="post-pagination__first">
      Первая
    </div>
    <div v-if="start !== 0" @click="prevPage" class="post-pagination__prev">
      Предыдущая
    </div>
    <div class="post-pagination__pages pages">
      <ul class="pages__list">
        <li @click.prevent="changePage(page)" v-for="page in totalPages" class="pages__item">
          <a :class="[ page === pageQuery ? 'pages__link pages__link_active': 'pages__link' ]" href="#">
            {{ page }}
          </a>
        </li>
      </ul>
    </div>
    <div v-if="start + 10 !== allPosts" @click="nextPage" class="post-pagination__next">
      Следующая
    </div>
    <div v-if="start + 10 !== allPosts" @click="lastPage" class="post-pagination__last">
      Последняя
    </div>
  </div>
</template>

<script>
  export default {
    name: 'PostPagination',
    props: {
      start: {
        type: Number,
        default: null
      },
      totalPages: {
        type: Number,
        default: null
      },
      allPosts: {
        type: Number,
        default: null
      }
    },
    data: () => ({}),
    computed: {
      pageQuery(){
        return parseInt(this.$route.query.page) || 1
      }
    },
    created() {

    },
    methods: {
      firstPage() {
        this.$emit('page', 1)
      },
      prevPage() {
        this.$emit('prev')
      },
      changePage(page) {
        this.$emit('page', page)
      },
      nextPage() {
        this.$emit('next')
      },
      lastPage() {
        this.$emit('page', 10)
      }
    }
  }
</script>

<style lang="scss" scoped>
  .post-pagination {
    display: flex;
    margin-top: 80px;
    align-items: baseline;

    &__first, &__prev, &__next, &__last {
      font-family: Open Sans, sans-serif;
      font-size: 13px;
      line-height: 25px;
      padding: 11px 20px 4px 18px;
      cursor: pointer;
    }
  }

  .pages {
    display: flex;
    justify-content: center;

    &__list {
      list-style: none;
      padding: 0;
      margin: 0;
    }

    &__item {
      display: inline-block;
      margin-right: 4px;
    }

    &__link {
      padding: 11px 14px 4px 13px;
      font-family: Open Sans, sans-serif;
      font-size: 13px;
      line-height: 25px;
      text-decoration: none;
      color: #000000;

      &_active {
        color: rgba(0, 0, 0, 0.2);
      }
    }
  }

</style>

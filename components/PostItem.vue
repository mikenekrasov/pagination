<template>
  <div class="post">
    <nuxt-link :to="{name: 'post-id', params: {id: post.id, post: post}}" class="post__link">
      <h2 class="post__title">
        {{ post.title }}
      </h2>
    </nuxt-link>
    <div v-if="isShow" class="post__content">
      {{ post.body }}
    </div>
    <div class="post__date">
      22.06.2018 в 16:44, изменена 23.06.2018 в 11:10
    </div>
    <span @click="contentToggle" :class="[isShow ? 'post__arrow post__arrow_active' : 'post__arrow']"></span>
  </div>
</template>

<script>
  export default {
    name: 'PostItem',
    props: {
      post: {
        type: Object,
        default: () => ({})
      }
    },
    data: () => ({
      isShow: false
    }),
    methods: {
      contentToggle() {
        this.isShow = !this.isShow
      }
    }
  }
</script>

<style lang="scss">
  .post {
    border: 1px solid rgba(0, 0, 0, 0.1);
    padding: 25px 130px 32px 37px;
    border-radius: 5px;
    margin-top: 10px;
    position: relative;

    &:first-child {
      margin-top: 46px;
    }

    &__arrow {
      content: '';
      position: absolute;
      width: 16px;
      height: 11px;
      top: 36px;
      right: 40px;
      background: url("~assets/arrow.png");
      transition: all .2s ease-in-out;
      cursor: pointer;

      &_active {
        transform: rotate(180deg);
      }
    }

    &__title {
      font-family: Open Sans, sans-serif;
      font-style: normal;
      font-weight: 600;
      font-size: 25px;
      line-height: 32px;
    }

    &__link {
      text-decoration: none;
      color: #000000;
    }

    &__date {
      margin-top: 16px;
      color: rgba(0, 0, 0, .5);
    }

    &__content {
      margin-bottom: 24px;
      margin-top: 15px;
    }
  }

</style>

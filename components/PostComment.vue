<template>
  <li class="comments__item">
    <div class="comments__title">{{ comment.name }}</div>
    <div class="comments__subtitle">{{ comment.email }}</div>
    <div class="comments__content">{{ comment.body }}</div>
  </li>
</template>

<script>
  export default {
    name: 'PostComment',
    props: {
      comment: {
        type: Object,
        default: () => ({})
      }
    },
    data: () => ({})

  }
</script>

<style lang="scss" scoped>
  .comments {

    &__item {
      padding: 25px 20px 25px 68px;
      border: 1px solid rgba(0, 0, 0, 0.1);
      border-radius: 5px;
      margin-top: 5px;
      position: relative;

      &:before {
        content: '';
        position: absolute;
        background: url("~assets/avatar.png");
        top: 24px;
        left: 20px;
        width: 40px;
        height: 42px;
      }
    }

    &__title {
      font-family: Open Sans, sans-serif;
      font-size: 15px;
      line-height: 22px;
    }

    &__subtitle {
      font-family: Open Sans, sans-serif;
      font-size: 13px;
      line-height: 22px;
      color: #BCBEC0;
    }

    &__content {
      margin-top: 10px;
    }
  }
</style>

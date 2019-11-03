<template>
  <section class="section">
    <div class="container section__container">
      <h1 class="section__title">Лента проектов</h1>
      <posts-list/>
    </div>
  </section>
</template>

<script>
  import postsList from '~/components/postsList'

  export default {
    components: {
      postsList
    }
  }
</script>

<style lang="scss">
  .container {
    margin: 0 auto;
    width: 970px;
  }

  .section {
    margin-top: 60px;

    .section__title {
      font-family: "Open Sans", sans-serif;
      font-weight: bold;
      font-size: 45px;
      line-height: 50px;
    }
  }

</style>

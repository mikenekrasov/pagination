<template>
  <footer class="footer">
    <div class="footer__main">
      <div class="container footer__container">
        <div class="footer__col">
          <header class="footer__header">
            О сервисе
          </header>
          <ul class="footer__menu">
            <li class="footer__item">
              <a href="#" class="footer__link">
                Заказчикам
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Исполнителям
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Самозанятым
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Партнерская программа
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Реклама на сайте
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Помощь
              </a>
            </li>
          </ul>
        </div>
        <div class="footer__col">
          <header class="footer__header">
            О нас
          </header>
          <ul class="footer__menu">
            <li class="footer__item">
              <a href="#" class="footer__link">
                История компании
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Реквизиты
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Частным лицам
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Партнерская программа
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Реклама на сайте
              </a>
            </li>
            <li class="footer__item">
              <a href="#" class="footer__link">
                Помощь
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <div class="footer__bottom">
      <div class="container">
        <div class="footer__copyright copyright">
          © 2018 Впроекте
        </div>
      </div>
    </div>

  </footer>
</template>

<script>
  export default {
    name: 'TheFooter'
  }
</script>

<style lang="scss" scoped>
  .footer {
    margin-top: 158px;

    &__main {
      margin-bottom: 107px;
    }

    &__container {
      display: flex;
      flex-flow: row wrap;
      justify-content: space-between;
    }

    &__col {
      flex: 1;
    }

    &__header {
      font-family: Open Sans, sans-serif;
      font-size: 13px;
      line-height: 20px;
    }

    &__menu {
      display: flex;
      flex-flow: column wrap;
      height: 66px;
      margin-top: 20px;
      padding-left: 0;
      list-style: none;
    }

    &__item {

    }

    &__link {
      font-family: Open Sans, sans-serif;
      font-size: 13px;
      line-height: 20px;
      color: #555555;
      text-decoration: none;
    }

    &__copyright {
      font-size: 13px;
      line-height: 18px;
      color: #BCBEC0;
      margin-bottom: 64px;
    }
  }
</style>

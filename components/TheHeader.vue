<template>
  <header class="header">
    <div class="container header__container">
      <a href="/" class="logo header__logo">
        Компания
      </a>
      <nav class="menu header__menu">
        <ul class="menu__list">
          <li class="menu__item">
            <a class="menu__link menu__link_active" href="#">Проекты</a>
          </li>
          <li class="menu__item">
            <a class="menu__link" href="#">Задачи</a>
          </li>
          <li class="menu__item">
            <a class="menu__link" href="#">Новости</a>
          </li>
          <li class="menu__item">
            <a class="menu__link" href="#">Вакансии</a>
          </li>
          <li class="menu__item">
            <a class="menu__link" href="#">Контакты</a>
          </li>
        </ul>
      </nav>
    </div>
  </header>
</template>

<script>
  export default {
    name: 'TheHeader'
  }
</script>

<style lang="scss" scoped>
  .header {
    padding: 40px 0;
    &__container {
      display: flex;
      align-items: baseline;
      justify-content: space-around;
      flex-wrap: wrap;
    }

    &__logo {
      font-family: 'Montserrat',sans-serif;
      font-size: 25px;
      line-height: 35px;
      font-weight: bold;
      text-transform: uppercase;
      color: #000000;

      text-decoration: none;
     }
    &__menu {
      margin-left: auto;
    }
  }
  .menu {
    &__list {
      padding-left: 0;
      list-style: none;
      display: flex;
    }
    &__link {
      font-family: "Open Sans",sans-serif;
      font-size: 15px;
      line-height: 22px;
      color: #000000;
      text-decoration: none;
      padding: 0 1.6em;

      &_active {
        font-weight: bold;
      }
    }
  }

</style>

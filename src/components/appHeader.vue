<template>

  <header>
    <div class="header__container">

      <a href="/" class="header__container__logo">
        <img src="../assets/app-logo.png" alt="Logo da Aplicação" class="header__container__logo__img">
      </a>

      <div class="header__container__title">
        <h1 class="header__container__title__text">Controle Financeiro</h1>
      </div>

      <a href="javascript:void(0)" class="header__container__menu-icon">
        <img src="../assets/menu-icon.png" v-on:click="menuShow" alt="ícone do menu" class="header__container__menu-icon__img">
      </a>

    </div>
  </header>

</template>

<script>
export default {
  name: 'appHeader',
  data() {
    return {}
  },
  methods: {
    menuShow() { this.$emit('menuShow'); }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  align-items: center;
  background-color: #E0E0E0;
  display: flex;
  justify-content: center;
  width: 100%;
}

.header__container {
  padding: 10px 15px;
  align-content: center;
  display: flex;
  justify-content: space-between;
  margin: 0 auto;
  max-width: 1100px;
  width: 100%;
}

.header__container__logo,
.header__container__title,
.header__container__menu-icon {
  display: flex;
  align-items: center;
}


.header__container__title__text {
  font-size: 20px;
  margin: 0;
}

.header__container__logo__img { width: 40px; }
.header__container__menu-icon__img { width: 30px; }
</style>

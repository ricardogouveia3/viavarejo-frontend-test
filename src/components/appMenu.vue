<template>

  <div class="menu">


    <nav>
    <a href="javascript:void(0)" class="menu__close" v-on:click="menuHidden">
      <img src="../assets/menu-close.png" alt="Ícone de fechar menu" class="menu__close__img">
    </a>
      <ul>
        <li>
          <a href="">Resumo</a>
        </li>
        <li>
          <a href="">Dashboard</a>
        </li>
        <li>
          <a href="">Configurações</a>
        </li>
      </ul>
    </nav>

  </div>

</template>

<script>
export default {
  name: 'appMenu',
  data() {
    return {}
  },
  methods: {
    menuHidden() { this.$emit('menuHidden'); }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.menu {
  box-sizing: border-box;
  position: absolute;
  min-width: 260px;
  right: 0;
  top: 0;
  min-height: 100vh;
  height: 100%;
  color: #fff;
  background-color: #333;
  display: inline-block;
}

nav {
  height: 100%;
  min-height: 100vh;
  position: relative;
}

.menu__close {
  position: absolute;
  top: 10px;
  left: 15px;
}
.menu__close__img { width: 35px; }

ul {
  display: flex;
  flex-direction: column;
  text-align: right;
  list-style: none;
  padding: 0;
  margin: 0;
  padding-top: 50px;
}

li:hover { background-color: #fff; }

li a {
  padding: 10px 8px;
  color: #fff;
  display: block;
  text-decoration: none;
}
li:hover a { color: #333; }

</style>

<template>
  <header class="navbar">
    <img class="logo-img" src="../../assets/images/group-12.png" srcset="../../assets/images/group-12@2x.png 2x, ../../assets/images/group-12@3x.png 3x">

    <nav class="auth-nav">
      <img class="user-img" src="../../assets/images/user.png" srcset="../../assets/images/user@2x.png 2x, ../../assets/images/user@3x.png 3x">
      <a href="#" class="auth-link">Entrar</a>
      <div class="divider" />
      <a href="#" class="auth-link">Criar conta</a>
    </nav>
  </header>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
.navbar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 0 10%;
  height: 100px;
  position: relative;
  .logo-img {
    width: 130px;
  }
  .auth-nav {
    display: grid;
    grid-template-columns: repeat(4, auto);
    align-items: center;
    grid-gap: 12px;
    z-index: 2;
    .user-img {
      width: 16px;
      margin-right: 7px;
    }
    .auth-link {
      font-weight: 700;
      color: #454344;
      text-decoration: none;
    }
    .auth-link:hover {
      text-decoration: underline;
    }
    .divider {
      width: 2px;
      height: 14px;
      background-color: #454344;
    }
  }
}

@media only screen and (max-width: 480px) {
  .navbar {
    justify-content: flex-end;
    .logo-img {
      position: absolute;
      left: 0;
      right: 0;
      margin: auto;
      width: 100px;
    }
    .auth-nav {
      grid-template-columns: auto;
      .user-img {
        width: 18px;
        margin-right: 0;
      }
      .auth-link {
        display: none;
      }
      .divider {
        display: none;
      }
    }
  }
}
</style>

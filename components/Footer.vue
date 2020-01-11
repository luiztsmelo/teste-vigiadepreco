<template>
  <footer>
    <section class="download-links-container">
      <div class="chrome-extension-wrapper">
        <img class="chrome-img" src="../assets/images/chrome.png">
        <p class="text">
          <b>Instale a extensão no seu Google Chrome</b> Texto de suporte do título
        </p>
      </div>

      <div class="app-download-links">
        <p class="text">
          <b>Baixe nosso app</b> e não fique de fora do que acontece no produto
        </p>
        <div class="links">
          <a class="link" href="https://play.google.com/" target="__blank">
            <img class="link-img" src="../assets/images/google-play.png" alt="Download na Google Play">
          </a>
          <a class="link" href="https://www.apple.com/ios/app-store/" target="__blank">
            <img class="link-img" src="../assets/images/app-store.png" alt="Download na App Store">
          </a>
        </div>
      </div>
    </section>

    <section class="nav-links-container">
      <nav>
        <span class="label">Sobre</span>
        <a href="#" class="link">Quem somos</a>
        <a href="#" class="link">Imprensa</a>
        <a href="#" class="link">Trabalhe conosco</a>
        <a href="#" class="link">Política de Privacidade</a>
      </nav>
      <nav>
        <span class="label">Destaques</span>
        <a href="#" class="link">Black Friday</a>
        <a href="#" class="link">Black Night</a>
        <a href="#" class="link">Dia dos Pais</a>
        <a href="#" class="link">Dia dos Namorados</a>
      </nav>
      <nav>
        <span class="label">Contato</span>
        <a href="#" class="link">Fale conosco</a>
        <a href="#" class="link">Mídia Kit / Parceria</a>
        <a href="#" class="link">Dúvidas frequentes</a>
      </nav>
      <nav>
        <span class="label">Redes sociais</span>
        <div class="social-media-links">
          <a href="#" class="link">
            <img class="link-img" src="../assets/images/facebook.svg" alt="Facebook">
          </a>
          <a href="#" class="link">
            <img class="link-img" src="../assets/images/twitter.svg" alt="Twitter">
          </a>
          <a href="#" class="link">
            <img class="link-img" src="../assets/images/instagram.svg" alt="Instagram">
          </a>
          <a href="#" class="link">
            <img class="link-img" src="../assets/images/youtube.svg" alt="Youtube">
          </a>
        </div>
      </nav>
    </section>

    <section class="stores-container">
      <p class="text">
        Lojas: Adidas, Americanas, Apple, Azul, Baby, Bebê Store, Beleza na Web, Camisaria Colombo, Carrefour, Casas Bahia, Centauro, Cipela, Cissa Magazine, Dafiti, Decathlon, Dell, eFácil, Época Cosméticos, Extra, Fast Shop, Fnac, Girafa, Insinuante, Kabum, Kanui, Lenovo, Livraria Saraiva, Magazine Luiz, Marisa, MegaMamute, Mobly, Netshoes, Nike, Ponto Frio, Posthaus, Ricardo Eletro, Sépha Perfumaria, Sephora, Shopfato, Shoptime, Sony, Sou Barato, Submarino Viagens, Super Muffato. <b>Se sua marca não está listada, entre em contato com a nossa equipe.</b>
      </p>
    </section>
  </footer>
</template>

<script>
export default {
}
</script>

<style lang="scss" scoped>
footer {
  margin-top: 2rem;
  .download-links-container {
    display: grid;
    grid-template-columns: auto auto;
    align-items: center;
    grid-gap: 120px;
    background-color: #A5D207;
    padding: 28px 10%;
    .text {
      color: #000;
    }
    .chrome-extension-wrapper {
      display: grid;
      grid-template-columns: auto 1fr;
      align-items: center;
      grid-gap: 15px;
      .chrome-img {
      }
    }
    .app-download-links {
      display: grid;
      grid-template-columns: 1fr auto auto;
      align-items: center;
      grid-gap: 15px;
      .links {
        display: grid;
        grid-template-columns: auto auto;
        grid-gap: 15px;
        align-items: center;
        .link {
          display: flex;
          align-items: center;
          .link-img {
            height: 43px;
          }
        }
      }
    }
  }
  .nav-links-container {
    display: grid;
    grid-template-columns: 1fr 1fr 1fr 1fr;
    align-items: start;
    grid-gap: 40px;
    background-color: #415400;
    color: #fff;
    padding: 28px 10%;
    nav {
      display: flex;
      flex-direction: column;
      .label {
        font-size: 17px;
        font-weight: 700;
        padding-bottom: 10px;
      }
      .link {
        text-decoration: none;
        color: #fff;
        font-size: 14px;
        margin: 4px 0;
      }
      .link:hover {
        text-decoration: underline;
      }
      .social-media-links {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        .link {
          .link-img {
            width: 32px;
            transition: cubic-bezier(0.455, 0.03, 0.515, 0.955) all .22s;
          }
          .link-img:hover {
            filter: brightness(85%);
          }
        }
      }
    }
  }
  .stores-container {
    background-color: #415400;
    color: #fff;
    padding: 6px 10% 20px;
    .text {
      font-size: 13px;
      line-height: 18px;
    }
  }
}

@media only screen and (max-width: 480px) {
  footer {
    .download-links-container {
      display: grid;
      grid-template-columns: 1fr;
      align-items: center;
      grid-gap: 120px;
      padding: 28px 7%;
      .text {
        text-align: center;
      }
      .chrome-extension-wrapper {
        display: none;
      }
      .app-download-links {
        display: grid;
        grid-template-columns: 1fr;
        align-items: center;
        justify-items: center;
        grid-gap: 15px;
        .links {
          display: flex;
          align-items: center;
          justify-content: space-between;
          .link {
            margin: 0 5px;
            .link-img {
              height: 40px;
            }
          }
        }
      }
    }
    .nav-links-container {
      grid-template-columns: 1fr;
      align-items: center;
      justify-items: center;
      grid-gap: 20px;
      padding: 28px 7%;
      nav {
        .label {
          text-align: center;
        }
        .link {
          text-align: center;
        }
        .link:hover {
        }
        .social-media-links {
          grid-gap: 15px;
          .link {
            .link-img {
            }
            .link-img:hover {
            }
          }
        }
      }
    }
    .stores-container {
      padding: 6px 7% 20px;
      .text {
        text-align: center;
      }
    }
  }
}
</style>

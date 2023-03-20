<template>
  <div class="background">
    <div class="header">
      <img class="logo" src="../assets/images/logo.png" alt="logo" />
      <div class="sign-wrapper">
        <button @click="store.toggleSignIn(true)" class="button sign-in-button">
          Вхід
        </button>
        <button @click="store.toggleSignUp(true)" class="button sign-up-button">
          Реестрація
        </button>
      </div>
    </div>

    <main class="main">
      <div class="about">
        <h3 class="title">
          <img class="hand" src="../assets/images/hand.png" alt="" />
          Володарі Трафіку
          <img class="hand flipped" src="../assets/images/hand.png" alt="" />
        </h3>
        <p class="paragraph">
          SC Partners – нова партнерська мережа з величезним досвідом та
          експертизою. Кожен наш партнер отримує очікувану вигоду на абсолютно
          прозорих умовах та бездоганний супровід. Ми будемо поряд з вами: на
          відстані одного повідомлення в месенджері або дзвінка, адже ми
          працюємо поряд з вами.
        </p>
        <img class="stars" src="../assets/images/stars.png" alt="start" />
      </div>

      <div class="info">
        <h4 class="dividing-title">Тим, хто нагоняє Траф</h4>
        <div class="cards">
          <div class="card" v-for="card in cards" :key="card.title">
            <div class="icon">
              <!-- prettier-ignore -->
              <img :src="card.img" alt="" />
            </div>
            <div class="text-wrapper">
              <h6 class="title">{{ card?.title }}</h6>
              <p class="subtext">{{ card.subtext }}</p>
            </div>
          </div>
        </div>
      </div>
    </main>

    <div class="popup" v-if="store.signInOpen || store.signUpOpen">
      <SignIn v-if="store.signInOpen" />
      <SignUp v-if="store.signUpOpen" />
    </div>
  </div>
</template>

<script>
import { reactive } from "vue";
import SignIn from "../components/SignIn.vue";
import SignUp from "../components/SignUp.vue";
import loudIcon from "../assets/images/loud.svg";
import emodjiIcon from "../assets/images/emodji.svg";
import chartIcon from "../assets/images/chart.svg";

export default {
  name: "SR",
  components: {
    SignIn: SignIn,
    SignUp: SignUp,
  },
  data() {
    return {
      store,
      cards: [
        {
          img: loudIcon,
          title: "Круті акції, призи та прибуткова\nбонусна програма",
          subtext:
            "Ми постійно працюємо над тим, щоб вам було цікаво та вигідно!",
        },
        {
          img: emodjiIcon,
          title: "Особлива підтримка\nдля кожного 24/7",
          subtext: "У вас буде свій персональний менеджер",
        },
        {
          img: chartIcon,
          title: "Детальна\nстатистика",
          subtext:
            "Миттєве оновлення, зрозуміла система відображення статистики",
        },
      ],
    };
  },
};

export const store = reactive({
  signInOpen: false,
  signUpOpen: false,
  toggleSignIn(value) {
    this.signInOpen = value;
    this.signUpOpen = false;
  },
  toggleSignUp(value) {
    this.signUpOpen = value;
    this.signInOpen = false;
  },
  showPassword: false,
  togglePassword(value) {
    this.showPassword = value;
  },
});
</script>

<style>
body {
  margin: 0 !important;
  background: #141416;
  color: #fff;
}

@font-face {
  font-family: "Gilroy";
  src: local("Gilroy"),
    url("./assets/fonts/Gilroy/Gilroy-Medium.eot") format("embedded-opentype"),
    url("./assets/fonts/Gilroy/Gilroy-Medium.ttf") format("truetype"),
    url("./assets/fonts/Gilroy/Gilroy-Medium.woff") format("woff"),
    url("./assets/fonts/Gilroy/Gilroy-Medium.woff2") format("woff2");
  font-weight: normal;
  font-style: normal;
}

@font-face {
  font-family: "Gilroy-Semibold";
  src: local("Gilroy"),
    url("./assets/fonts/Gilroy/Gilroy-Semibold.eot") format("embedded-opentype"),
    url("./assets/fonts/Gilroy/Gilroy-Semibold.ttf") format("truetype"),
    url("./assets/fonts/Gilroy/Gilroy-Semibold.woff") format("woff"),
    url("./assets/fonts/Gilroy/Gilroy-Semibold.woff2") format("woff2");
  font-weight: bolder;
  font-style: normal;
}
</style>

<style lang="scss">
#__nuxt {
  text-align: center;
  background: #141416;
  color: #fff;
  font-family: "Gilroy";
  overflow-x: hidden;

  .background {
    padding: 0 0 100px;
    min-height: 100vh;
    width: 100vw;
    background: url("./assets/images/bg.png");
    background-size: 100% 100%;

    @media all and (max-width: 376px) {
      padding: 0;
    }

    .header {
      padding: 0 24px;
      height: 93px;
      background: #141416;
      border-bottom: 1px solid #23262f;

      display: flex;
      align-items: center;
      justify-content: space-between;
      box-sizing: border-box;

      .logo {
        width: 148px;
      }

      &::before {
        content: "";
        width: 180px;
      }

      @media all and (max-width: 376px) {
        padding: 0 16px;

        .button {
          font-size: 14px;
        }

        &::before {
          content: none;
        }
      }
    }

    .main {
      .about {
        margin: 100px auto 0;
        height: 263px;
        width: 900px;
        background: rgba(35, 38, 47, 50%);
        border-radius: 24px;

        .title {
          font-family: "Gilroy";
          margin: 0;
          padding: 39px 0 25px;
          display: flex;
          justify-content: center;
          align-items: center;
          gap: 25px;
          font-size: 40px;
          .hand.flipped {
            transform: scaleX(-1);
          }

          @media all and (max-width: 376px) {
            padding: 25px 0;
            gap: 10px;
            font-size: 25px;

            img {
              height: 25px;
            }
          }
        }

        .paragraph {
          margin: 0 44px 25px;
          color: #b1b5c3;

          @media all and (max-width: 376px) {
            margin: 0 25px 25px;
            line-height: 24px;
            font-size: 14px;
          }
        }

        @media all and (max-width: 376px) {
          margin: 50px auto;
          height: 342px;
          width: calc(100% - 30px);
        }
      }

      .dividing-title {
        margin: 125px 0 75px;
        font-family: "Gilroy";
        font-size: 32px;

        @media all and (max-width: 376px) {
          margin: 50px 0 35px;
          font-size: 25px;
        }
      }

      .cards {
        margin: auto;
        display: flex;
        gap: 7%;
        width: 83%;
        box-sizing: border-box;

        .card {
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          width: 28%;
          max-width: 345px;

          .icon {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 65px;
            width: 65px;
            background: #ffc737;
            border-radius: 15px;
          }

          .text-wrapper {
            .title {
              font-weight: normal;
              margin: 25px 0;
              line-height: 24px;
              font-size: 16px;
            }

            .subtext {
              margin: 0;
              color: #777e90;
              font-size: 14px;
            }
          }

          @media all and (max-width: 376px) {
            gap: 25px;
            flex-direction: row;
            width: 100%;

            .icon {
              height: 45px;
              width: 45px;

              img {
                height: 25px;
              }
            }

            .text-wrapper {
              width: 245px;
              text-align: left;

              .title {
                margin: 0 0 5px;
              }
            }
          }
        }

        @media all and (max-width: 376px) {
          gap: 25px;
          flex-direction: column;
          width: calc(100% - 30px);
        }
      }

      @media all and (max-width: 376px) {
        display: flex;
        flex-direction: column-reverse;
      }
    }
  }

  .popup {
    position: fixed;
    top: 0;
    height: 100%;
    width: 100vw;
    background: rgb(53 57 69 / 85%);

    &_sign-in {
      position: absolute;
      top: calc(50vh - 124px);
      left: calc(50vw - 177.5px);
      height: 284px;
      width: 355px;
      background: #23262f;
      border-radius: 25px;

      @media all and (max-width: 376px) {
        top: calc(100vh - 294px);
      }

      .close-button {
        position: absolute;
        top: 10px;
        right: 10px;
        display: flex;
        justify-content: center;
        align-items: center;
        height: 40px;
        width: 40px;
        background: #2a2e38;
        border: none;
        border-radius: 40px;
      }

      &-header {
        display: flex;
        gap: 10px;
        margin: 25px 0 0 30px;
        height: 45px;
        align-items: center;
        .icon {
          display: flex;
          padding: 10px;
          justify-self: center;
          align-items: center;
          height: 25px;
          width: 25px;
          background: #ff6838;
          border-radius: 15px;
        }
        .title {
          font-weight: bolder;
          font-size: 25px;
        }
      }
    }
  }
}

button,
.button {
  padding: 0 16px;
  height: 40px;
  border-radius: 90px;
  font-family: "Gilroy";
  cursor: pointer;
  border: none;
  background: #ffc737;
  outline: none;

  &.sign-up-button {
    background: #ffc737;
  }

  &.sign-in-button {
    border: 2px solid #777e90;
    background: none;
    color: #fff;
    margin-right: 15px;

    @media all and (max-width: 376px) {
      margin-right: 10px;
    }

    &:hover {
      background: rgb(255 255 255 / 10%);
    }

    &:active {
      background: rgb(255 255 255 / 20%);
    }
  }
}

.form {
  margin: 25px auto;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 10px;
  width: calc(100% - 60px);

  .submit {
    width: 88px;
  }
}

.input-wrapper {
  position: relative;
  width: 100%;

  .toggle-password {
    cursor: pointer;
    position: absolute;
    top: 16px;
    right: 16px;
  }
}

.input {
  padding: 16px;
  width: calc(100% - 3px);
  height: 48px;
  background: #23262f;
  border: 2px solid #777e90;
  border-radius: 70px;
  color: #777e90;
  font-weight: bolder;
  box-sizing: border-box;
  outline: none;
}

::selection {
  color: #23262f;
  background: #ff8b6f;
}

::-moz-selection {
  color: #23262f;
  background: #ff8b6f;
}
</style>

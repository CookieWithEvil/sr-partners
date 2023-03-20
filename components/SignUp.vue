<template>
  <div class="sign-up">
    <button class="close-button" @click="store.toggleSignUp(false)">
      <img src="../assets/images/close.png" alt="close" />
    </button>

    <div class="left side">
      <h3>
        Зможеш обрати <br />
        свій варіант
      </h3>

      <div class="pseudoul">
        <div class="pseudoli">
          <div class="divider">
            <img src="../assets/images/check.png" alt="" />
          </div>
          <h5 class="text title">CPA</h5>
          <p class="text info">$25 і вище</p>
        </div>

        <div class="pseudoli">
          <div class="divider">
            <img src="../assets/images/check.png" alt="" />
          </div>
          <h5 class="text title">REVSHARE</h5>
          <p class="text info">Піднімай до 60%</p>
        </div>

        <div class="pseudoli">
          <div class="divider">
            <img src="../assets/images/check.png" alt="" />
          </div>
          <h5 class="text title">Гібрид</h5>
          <p class="text info">Зробимо як скажеш</p>
        </div>
      </div>

      <nav class="nav">
        <button class="transparent-button">
          <img class="arrow" src="../assets/images/arrow.svg" alt="" />
        </button>
        <button class="transparent-button bullet active" />
        <button class="transparent-button bullet" />
        <button class="transparent-button bullet" />
        <button class="transparent-button">
          <img class="arrow right" src="../assets/images/arrow.svg" alt="" />
        </button>
      </nav>
    </div>

    <div class="right side">
      <div class="side-header">
        <img class="person-icon" src="../assets/images/person.svg" alt="" />
        <h3>Реестрація</h3>
      </div>
      <form class="form">
        <input
          type="text"
          v-model="text"
          class="input"
          placeholder="Вашe Ім'я"
        />
        <input
          type="text"
          v-model="text"
          class="input"
          placeholder="Ваш email"
        />
        <label class="input-wrapper">
          <input
            :type="store.showPassword ? 'text' : 'password'"
            v-model="password"
            class="input"
            placeholder="Ваш пароль"
          />
          <img
            class="toggle-password"
            @click="store.togglePassword(!store.showPassword)"
            src="../assets/images/eye.svg"
            alt="toggle"
          />
        </label>
        <label class="input-wrapper">
          <input
            :type="store.showPassword ? 'text' : 'password'"
            v-model="password"
            class="input"
            placeholder="Повторіть пароль"
          />
          <img
            class="toggle-password"
            @click="store.togglePassword(!store.showPassword)"
            src="../assets/images/eye.svg"
            alt="toggle"
          />
        </label>
        <div class="communication-method">
          <h5 class="title">ОБЕРІТЬ СПРОСІБ ЗВЯЗКУ</h5>
          <div class="wrapper">
            <button class="method-button">
              <img src="../assets/images/telegram.png" alt="" />
            </button>
            <button class="method-button">
              <img src="../assets/images/skype.png" alt="" />
            </button>
            <input
              type="text"
              v-model="text"
              class="input"
              placeholder="@телеграм_адреса"
            />
          </div>
        </div>
        <button class="button submit">Реєстрація</button>
      </form>
    </div>
  </div>
</template>

<script>
import { store } from "../pages/index.vue";

export default {
  data() {
    return {
      store,
    };
  },
};
</script>

<style lang="scss">
.sign-up {
  position: absolute;
  top: calc(50% - 300px);
  left: calc(50% - 385px);
  height: 600px;
  width: 770px;
  background: #23262f;
  border-radius: 25px;

  @media all and (max-width: 376px) {
    height: auto;
    min-height: 510px;
    width: calc(100% - 30px);
    left: 15px;
    bottom: 15px;
    top: unset;
  }
}

.side {
  height: 600px;
  width: 50%;
  float: left;

  @media all and (max-width: 376px) {
    height: auto;
    min-height: 510px;
  }

  &.left {
    border-radius: 25px 0 0 25px;
    background: #58bd7d url("../assets/images/green-background.png");

    h3 {
      margin: 65px 0 0 53px;
      font-weight: 400;
      text-align: left;
      line-height: 40px;
      font-size: 25px;
    }

    .pseudoul {
      display: flex;
      flex-direction: column;
      gap: 25px;
      margin: 65px 0 0 53px;

      .pseudoli {
        display: block;
        .divider {
          margin: 0 25px 0 0;
          float: left;
          display: flex;
          justify-content: center;
          align-items: center;
          height: 45px;
          width: 45px;
          border-radius: 50%;
          background: #79ca97;
        }

        .text {
          margin: 0;
          text-align: left;
          font-size: 14px;

          &.title {
            line-height: 16px;
          }

          &.info {
            line-height: 24px;
          }
        }
      }
    }

    .nav {
      margin: 82px auto 0;
      height: 16px;
      width: 96px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      .transparent-button {
        padding: 0;
        background: none;
        border: none;

        .arrow.right {
          transform: scaleX(-1);
        }
      }

      .bullet {
        height: 8px;
        width: 8px;
        background: #e6e8ec;

        &.active {
          background: #ffd166;
        }
      }
    }

    @media all and (max-width: 376px) {
      display: none;
    }
  }

  &.right {
    .side-header {
      margin-top: 60px;
      .person-icon {
        padding: 10px;
        height: 25px;
        width: 25px;
        background: #58bd7d;
        border-radius: 15px;
      }

      @media all and (max-width: 376px) {
        display: flex;
        margin: 25px 25px 0;
        gap: 10px;
        align-items: center;
      }
    }

    .communication-method {
      .title {
        margin: 15px 0 0;
        color: #b1b5c3;
        font-size: 12px;
      }

      .wrapper {
        margin: 10px 0 15px;
        display: flex;
        gap: 10px;
        .method-button {
          background: #353945;
          height: 45px;
          width: 45px;
          display: flex;
          justify-content: center;
          align-items: center;
        }

        .input {
          width: 185px;
          text-align: center;
          color: #777e90;
        }
      }
    }

    .submit {
      font-family: "Gilroy-Semibold";
      font-weight: bolder;
      font-style: normal;
      width: 133px;
      font-weight: bolder;
    }

    @media all and (max-width: 376px) {
      width: 100%;
    }
  }
}

.close-button {
  background: #353945;
  width: 40px;
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 10px;
  right: 10px;
}
</style>

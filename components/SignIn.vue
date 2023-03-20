<template>
  <div>
    <div class="popup_sign-in">
      <button class="close-button" @click="store.toggleSignIn(false)">
        <img src="../assets/images/close.png" alt="close" />
      </button>
      <div class="popup_sign-in-header">
        <img class="icon" src="../assets/images/lock.svg" alt="" />
        <h4 class="title">Вхід</h4>
      </div>

      <form class="form">
        <input
          type="text"
          v-model="text"
          class="input"
          placeholder="Ваш email"
        />
        <label class="input-wrapper">
          <input
            :type="showInput ? 'text' : 'password'"
            v-model="password"
            class="input"
            placeholder="Ваш пароль"
          />
          <img
            class="toggle-password"
            @click="togglePassword(!store.showPassword)"
            src="../assets/images/eye.svg"
            alt="toggle"
          />
        </label>
        <button class="button submit">Війти</button>
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

<style lang="scss" scoped>
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
</style>

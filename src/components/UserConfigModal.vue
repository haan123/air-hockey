<template>
  <div id="user-config-modal" class="modal-container user-modal-container">
    <div class="modal-background">
      <div class="modal user-modal">
        <div class="user-modal__content">
          <div class="form-group">
            <label for="user-name">Enter Your Name</label>
            <input id="user-name" :ref="user" class="form-control" type="text" name="name" autocomplete="off">
          </div>
        </div>
        <button v-on:click="setUser" class="btn btn-dark user__start">Play</button>
      </div>
    </div>
  </div>
</template>

<script>
/* eslint no-plusplus: 0 */
/* eslint comma-dangle: 0 */
/* eslint class-methods-use-this: 0 */
/* eslint consistent-return: 0 */
/* eslint array-callback-return: 0 */

import modal from '../core/modal';

export default {
  props: ['game'],

  data() {
    return {
      user: 'user'
    };
  },

  methods: {
    setUser() {
      const user = this.$refs.user.value;
      localStorage.setItem('user', user);

      this.game.setUser(user);

      this.$parent.checkUser();

      modal.hideModal('user-config-modal');
    }
  }
};
</script>

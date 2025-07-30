<template>
  <div class="container-fluid absolute-center">
    <div class="row">
      <div class="col-md-12">
        <h5 class="text-center">
          Please log in with your GitHub profile to access ALBS
        </h5>
      </div>
    </div>
    <div class="row">
      <div class="col-md-12" style="display: grid">
        <q-btn
          flat
          text="Login with your GitHub profile"
          @click="githubLogin"
        >
          <q-icon class="text-dark" size="250px">
            <img
              src="~assets/github-mark.svg"
              alt="Login using your GitHub profile"
            />
          </q-icon>
        </q-btn>
      </div>
    </div>
  </div>
</template>

<script>
import { defineComponent } from 'vue'
import { fabGithub } from '@quasar/extras/fontawesome-v5'

export default defineComponent({
  name: 'LoginPage',

  setup() {
    return {
      fabGithub,
    }
  },

  methods: {
    githubLogin() {
      this.$api.get('/auth/github/authorize').then((response) => {
        window.location.href = response.data.authorization_url
      })
    },
  },
})
</script>

<style>
  .login-button {
    position: absolute;
    top: 50%;
    left: 50%;
    margin-top: -50px;
    margin-left: -50px;
  }

  .login-box {
    position: absolute;
    top: 50%;
    left: 50%;
    margin-top: -50px;
    margin-left: -50px;
  }
</style>

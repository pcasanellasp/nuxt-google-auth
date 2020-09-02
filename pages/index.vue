<template>
  <div class="container">
    <div>
      <Logo />
      <h1 class="title">
        Nuxt Google Auth
      </h1>
      {{ auth }}
      <div class="links">
        <SocialButton />
        <a
          href="#"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
          v-if="isAuth"
          @click.prevent="logout"
        >
          Logout
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters, mapState } from 'vuex';
export default {
  computed: {
    ...mapGetters([
      'isAuth',
      'auth',
    ])
  },
  methods: {
    async logout() {
      await this.$auth.logout()
    },
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>

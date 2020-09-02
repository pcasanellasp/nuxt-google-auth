<template>
  <a
    href="http://localhost:1337/connect/google"
    target="_blank"
    rel="noopener noreferrer"
    class="button--grey"
  >
    Login with Google
    {{$route.name}}
  </a>
</template>

<script>
export default {
  mounted(){
    window.onstorage = async (event) => {
      //TODO: Check if event.key === auth_token.local and event.oldValue === "false".
      // Refresh user on after localStorage change
      await this.$auth.setUserToken(window.localStorage.getItem('auth._token.local').replace('Bearer ', ''))

      // Check if this.$route.name is app-claim ('/nueva-reclamacion')
      // Dispatch action this.setNextStep('PassengerInfo')

      // Else if this.$route.name is auth-login ('/login')
      // this.$router.push(localePath('app-admin')) '/mis-reclamaciones'

    }
  },
}
</script>

<style>

</style>
<template>
  <div>Redirect</div>
</template>

<script>
export default {
 async mounted()  {
  const { access_token } = this.$route.query
  const { data } = await this.$axios.get('http://localhost:1337/auth/google/callback', { params: { access_token } }) // Remove this line if access_token is already user jwt 
  await this.$auth.setUserToken(data.jwt) // Replace data.jwt to access_token
  window.close()
 }
}
</script>

<style>

</style>
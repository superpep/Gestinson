<template>
  <q-page class="bg-secondary window-height window-width row justify-center items-center"/>
</template>

<script>
import { auth } from 'boot/firebase'
import { Notify } from 'quasar'
export default {
  name: 'signout',
  async created () {
    try {
      await auth.signOut()
      Notify.create({
        type: 'positive',
        message: this.$t('signout_ok')
      })
      this.$router.push({ name: 'login' })
    } catch (err) {
      Notify.create({
        type: 'negative',
        message: err.message
      })
    }
  }
}
</script>

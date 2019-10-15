<template>
  <div class="home">
    <vueLogin msg="App Questionnaire"/>
  </div>
</template>

<script>
// @ is an alias to /src
import vueLogin from '@/components/vueLogin.vue'

export default {
  name: 'home',
  components: {
    vueLogin
  }
}
</script>

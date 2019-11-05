<template>
  <div class="questionnaire">
    <vueQuestionnaire/>
  </div>
</template>

<script>
// @ is an alias to /src
import vueQuestionnaire from '@/components/vueQuestionnaire.vue'

export default {
  name: 'questionnaire',
  components: {
    vueQuestionnaire
  }
}
</script>

<template>
   <div class="container">
      <form id="contact">
        <fieldset>
        <h2>{{ questions[i].question }}</h2>
        </fieldset>
        <fieldset>
          <label class="container-radio" v-for="prop in questions[i].propositions" > 
            <input type="radio" name="radio" v-model="selected" v-bind:value="prop" >
            <span class="checkmark"></span>{{ prop }}
          </label>
        </fieldset>
        <div>Selected: <strong>{{ selected }}</strong></div>
      </form>
         <fieldset><button id="contact" type="submit"  @click="onSubmit" >Question suivante</button></fieldset>
  </div>
</template>

<script>

export default {
  name: 'vueQuestionnaire',
  data() {
    return {
      selected :'',
      questions : {},
      i:0,
      form: {
        prenom: this.$route.params.prenom,
        nom: this.$route.params.nom,
        societe: this.$route.params.societe,
        score:0,
      }, 
    }
  },

  created: function() {
    this.fetchData()
  },

  methods: {
    fetchData: function() {
      this.questions = require("../assets/question.json");
      //console.log(this.questions); // Test unitaire afin d'avoir un affichage des infos en console
    },
    onSubmit(evt) {
      //console.log(this.questions[this.i]);
      if (this.selected == this.questions[this.i].reponse) {
        this.form.score++;
      }
      if ( this.selected != '') {
        if (this.i < 10) {
          this.i++
        } else {
          this.$router.push({ name : 'resultat', params: this.form})
        }
      }
      this.selected='';
    },
  }
}
</script>

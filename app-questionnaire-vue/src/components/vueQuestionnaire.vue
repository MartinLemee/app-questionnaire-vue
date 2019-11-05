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
      selected :'', // Récupération de l'élément selectionné
      questions : {},
      i:0,
      form: {
        // Récupération du prenom,nom et societe via le form précédent
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
      // Récupération du json dans "questions" afin de pouvoir l'utiliser
      // exemple : questions.propositions nous donnera les propositions de la question
      this.questions = require("../assets/question.json");

      //console.log(this.questions); // Test unitaire afin d'avoir un affichage des infos en console
    },
    onSubmit(evt) {
      // Submit lorqu'on clique sur "suivant"

      //console.log(this.questions[this.i]);

      // Augmente le score si jamais la reponse saisie est la bonne
      if (this.selected == this.questions[this.i].reponse) {
        this.form.score++; 
      }
      // Jusqu'à 10 questions, vu qu'on en a que 10
      if ( this.selected != '') {
        if (this.i < 10) {
          this.i++
        } else {
          this.$router.push({ name : 'resultat', params: this.form}) // push vers resultat une fois toutes les questions finies
        }
      }
      this.selected='';
    },
  }
}
</script>

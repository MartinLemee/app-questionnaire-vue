<template>
<div>
     <div class="container">
    <form id="contact">
        <h3> {{ msg }} </h3>
        <fieldset>
          <h2>Question 1</h2>
        </fieldset>
        <fieldset>
            <input placeholder="r1" type="checkbox" v-model="r1" tabindex="1" > reponse 1
        </fieldset>
        <fieldset>
            <input placeholder="r2" type="checkbox" v-model="r2" tabindex="2" > reponse 2
        </fieldset>
        <fieldset>
            <input placeholder="r3" type="checkbox" v-model="r3" tabindex="3" > reponse 3
        </fieldset>
        <fieldset>
             <button name="submit" type="submit" id="contact-submit" >Suivant</button>
        </fieldset>
    </form>
  </div>
  </div>
</template>

<script>
export default {

  name: 'vueQuestionnaire',
  props: {
    msg: String
  }
}
</script>

<template>
  <div class="Resultat">
  	<!-- <pre>{{$route.params.score}}</pre> -->
    <h1>Résultat</h1>
    <fieldset>
      <h2>Prenom : {{$route.params.prenom}}</h2>
      <h2>Nom : {{$route.params.nom}}</h2>
      <h2>Société : {{$route.params.societe}}</h2>
      </fieldset>
    <h2>Score = {{$route.params.score}}/10</h2>
  </div>
</template>
<script>
  name: 'Resultat';
</script>
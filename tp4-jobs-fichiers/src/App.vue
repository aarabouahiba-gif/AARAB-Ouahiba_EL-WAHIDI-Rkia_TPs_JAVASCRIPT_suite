<template>
  <nav class="menu">
    <RouterLink to="/">Accueil</RouterLink>
    <RouterLink to="/add">Ajouter un emploi</RouterLink>
  </nav>
  <RouterView />
</template>

<style>
body { font-family: sans-serif; margin: 0; background: #f5f5f5; }
.menu { background: #42b883; padding: 1rem; }
.menu a { color: white; margin-right: 1rem; text-decoration: none; font-weight: bold; }
.page { max-width: 700px; margin: 2rem auto; padding: 0 1rem; }
.card { background: white; border-radius: 6px; padding: 1rem; margin-bottom: 1rem; }
button { padding: .4rem .8rem; cursor: pointer; margin-right: .5rem; }
.danger { background: #d9534f; color: white; border: none; }
input, textarea { margin-bottom: .6rem; padding: .3rem; width: 100%; box-sizing: border-box; }
</style>

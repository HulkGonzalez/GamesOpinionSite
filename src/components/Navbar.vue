<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href=""><i class="bi bi-headset"> Games Opinion</i></a>
        <button
          class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup"
          aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav">
            <router-link class="nav-link" to="/"
              ><i class="bi bi-house-fill"></i> Home</router-link>
            <router-link class="nav-link" to="/opiniones"
              ><i class="bi bi-chat-square-text-fill"></i> Opiniones </router-link>
            <router-link class="nav-link" to="/administracion"
              ><i class="bi bi-people-fill"></i> Administracion </router-link>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
.flex {
  justify-content: end;
}
.nav-link {
  font-size: 1.5rem;
}
</style>

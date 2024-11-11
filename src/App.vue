<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary shadow-sm">
      <div class="container">
        <!-- Título de la aplicación -->
        <router-link class="navbar-brand d-flex align-items-center" to="/">
          <img src="@/assets/logo.png" alt="Vue logo" width="30" height="30" class="d-inline-block align-top me-2" />
          Gestor de Tareas
        </router-link>

        <!-- Botón de toggler para pantallas pequeñas -->
        <button
          class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation"
        >
          <span class="navbar-toggler-icon"></span>
        </button>

        <!-- Contenido del navbar -->
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <!-- Elementos de navegación con iconos -->
            <li class="nav-item">
              <router-link class="nav-link d-flex align-items-center" to="/addtask">
                <i class="bi bi-plus-circle me-2"></i>Añadir Tarea
              </router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link d-flex align-items-center" to="/tasklist">
                <i class="bi bi-card-list me-2"></i>Lista de Tareas
              </router-link>
            </li>
            <li class="nav-item">
              <router-link class="nav-link d-flex align-items-center" to="/combined">
                <i class="bi bi-grid me-2"></i>Vista Combinada
              </router-link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  background-color: rgb(94, 94, 189);
}

.navbar {
  margin-bottom: 20px;
  background-color: rgb(71, 71, 134);
}

.nav-link {
  font-weight: bold;
  transition: color 0.3s;
}

.nav-link:hover {
  color: rgb(110, 153, 24);
}

.nav-link.nav-link.router-link-exact-active {
  color: rgb(60, 82, 15);
  text-decoration: underline;
}
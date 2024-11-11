<template>
  <div class="container mt-5">
    <div class="text-center">
      <h1 class="display-4 text-primary mb-4">Bienvenidos al gestor de Tareas</h1>
      <p class="lead text-secondary mb-4">
        Esta aplicación te permite gestionar tus tareas.
      </p>
      <img src="@/assets/logo.png" class="img-fluid mb-4 logo" alt="Vue logo" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'HomeView',
};
</script>

<style scoped>
.container {
  max-width: 900px;
}

.display-4 {
  border-radius: 50px;
  font-weight: bold;
  text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.2);
}
.logo {
  border-radius: 40px;
  box-shadow: 0 0 20px rgba(207, 35, 150, 0.5);
  transition: transform 0.3s, box-shadow 0.3s;
}

.logo:hover {
  transform: scale(1.1);
  box-shadow: 0 0 30px rgba(218, 40, 188, 0.7);
}

h2 {
  font-weight: bold;
}

.text-muted {
  font-size: 1rem;
}
.lead {
  font-size: 1.25rem;
}

</style>

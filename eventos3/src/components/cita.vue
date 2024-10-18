<template>
    <div :class="['card mb-4', getCardClass(gravedad)]">
      <div class="card-body">
        <h5 class="card-title">Cita</h5>
        <p><strong>Paciente:</strong> {{ paciente }}</p>
        <p><strong>Fecha:</strong> {{ fecha }}</p>
        <p><strong>Hora:</strong> {{ hora }}</p>
        <p><strong>Gravedad:</strong> {{ gravedad }}</p>
        <p><strong>Motivo:</strong> {{ motivo }}</p>
        <button @click="$emit('delete-cita', index)" class="btn btn-secondary">Eliminar</button>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo', 'index'],
    methods: {
      getCardClass(gravedad) {
        // Cambiar el color de la tarjeta según la gravedad
        switch (gravedad) {
          case 'baja':
            return 'bg-warning';
          case 'media':
            return 'bg-success';
          case 'alta':
            return 'bg-danger';
          default:
            return '';
        }
      }
    }
  };
  </script>
  
  <style scoped>
 
  
  .bg-warning {
    background-color: yellow;
  }
  .bg-success {
    background-color: green;
  }
  .bg-danger {
    background-color: red;
  }

  .card-body {
width: calc(25% - 20px);
border-radius: 1rem;
padding: 1rem;
}
  </style>
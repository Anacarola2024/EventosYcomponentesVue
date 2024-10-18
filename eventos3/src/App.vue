<script  >
import Cita from './components/cita.vue'; 

// Importar el componente hijo

export default {
  components: { Cita },
  data() {
    return {
      citas: [], // Lista de citas
      form: {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: ''
      }
    };
  },
  computed: {
    isFormValid() {
  return this.form.paciente && this.form.fecha && this.form.hora && this.form.gravedad && this.form.motivo;
}

  },
  methods: {
    onSubmit() {
      // Al enviar el formulario, agrega una nueva cita a la lista
      if (this.isFormValid) {
        this.citas.push({...this.form});
      }
      this.form = {
        paciente: '',
        fecha: '',
        hora: '',
        gravedad: '',
        motivo: ''
      };
    },
    deleteCita(index) {
      // Eliminar una cita de la lista
      if (this.citas.length === 0) {
        return;
    
      
    } 
      // Eliminar una cita de la lista
      this.citas.splice(index, 1);
    }
  }


  }



</script>

<template>

<div  class="col-md-6">
  
    <form @submit.prevent="onSubmit" class="form p-3 shadow-sm rounded border">
    
      <div class="col">
        <label :class="{'text-danger': !form.paciente}"for="paciente" class=" fw-bold">Paciente</label>
        <input v-model="form.paciente" id="paciente" type="text"  class="form-control" placeholder="Nombre del paciente">
      </div>
      <div class="col-md-6">
        <label :class="{'text-danger': !form.fecha}" for="fecha" class="form-label fw-bold">Fecha:</label>
        <input v-model="form.fecha"  id="fecha" type="date" class="form-control ">
      </div>
      <div class="col-md-6">
        <label :class="{'text-danger': !form.hora}"for="hora" class="form-label fw-bold">Hora:</label>
        <input v-model="form.hora" id="hora" type="time" class="form-control">
      </div>
      <div class="col-md-6">
        <label :class="{'text-danger': !form.gravedad}"for="gravedad" class="form-label fw-bold">Gravedad:</label>
        <select v-model="form.gravedad" id="gravedad" type ="text" class="form-control">
          <option value="" disabled>Seleccione gravedad</option>
          <option value="baja">Baja</option>
          <option value="media">Media</option>
          <option value="alta">Alta</option>
        </select>
      </div>
      <div class="col ">
        <label :class="{'text-danger': !form.motivo}" for="motivo" class="form-label fw-bold">Motivo:</label>
        <input v-model="form.motivo" id="motivo" type="text" class="form-control">
      </div>

      <div :class="Text-center">
      <button type="submit" class="btn btn-primary" :disabled="isFormValido">Agregar</button>
      </div>
    </form>

  

    <div v-if="citas.length === 0" class="mt-3">
      <p class="text-center text-danger"> Aún no hay consultas registradas</p>
    </div>

    
    <Cita
      v-for="(cita, index) in citas"
      :key="index"
      :paciente="cita.paciente"
      :fecha="cita.fecha"
      :hora="cita.hora"
      :gravedad="cita.gravedad"
      :motivo="cita.motivo"
      :index="index"
      @delete-cita="deleteCita"
    />
  </div>
  
</template>

<style scoped>








</style>

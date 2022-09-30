<template>
  <form @submit.prevent="registrarProyecto">
    <div class="mb-3">
      <label for="exampleInputEmail1" class="form-label">Proyecto</label>
      <input v-model.trim="proyecto"  type="text" class="form-control" required >
    </div>
    <div class="mb-3">
      <label for="exampleInputPassword1" class="form-label">Actividad</label>
      <select v-model.trim="tipo" class="form-select">
        <option selected>Selecciona una actididad</option>
        <option>Aplicaciones web con Vue.js</option>
        <option>BackEnd Services</option>
        <option>Three</option>
      </select>
    </div>
    <div class="form-check">
      <input v-model.trim="urgente" class="form-check-input" type="checkbox">
      <label class="form-check-label" for="flexRadioDefault1">
        Urgente
      </label>
    </div>

    <button type="submit" class="btn btn-primary">Guardar</button>
  </form>
  <hr>
  <div class="table-responsive">
    <table class="table table-dark">
      <thead>
        <tr>
          <th>#</th>
          <th>Proyecto</th>
          <th>Tipo</th>
          <th>Urgente</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(proyecto, clave) in proyectos" :key="clave">
          <td>{{clave+1}}</td>
          <td>{{proyecto.proyecto}}</td>
          <td>{{proyecto.tipo}}</td>
          <td class="bg-success" :class="proyecto.urgente ? 'bg-success' : 'bg-danger'">{{proyecto.urgente ? "Si" : "No"}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
  export default {
    data: () => ({
      proyecto: "",
      tipo: "",
      urgente: false,
      proyectos: [],
    }),
    methods: {
      registrarProyecto(){
        const proyecto = {
          proyecto: this.proyecto,
          tipo: this.tipo,
          urgente: this.urgente,
        };
        this.proyectos.push(proyecto)
        console.log(this.proyectos);

        this.proyecto = "";
        this.tipo = "";
        this.urgente = false;
      },
    },
  };

</script>
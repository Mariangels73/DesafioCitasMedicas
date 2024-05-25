<template>
  <div>
    <table border="ridge">
      <thead>
        <tr>
          <th>Paciente</th>
          <th>Fecha</th>
          <th>Hora</th>
          <th>Motivo</th>
          <th></th>
        </tr>
      </thead>

      <tbody>
        <tr
          v-for="({ paciente, fecha, hora, motivo, gravedad }, i) in consultas"
          :key="i"
          :class="{
            'bg-red': gravedad == 3,
            'bg-yellow': gravedad == 2,
            'bg-green': gravedad == 1,
          }"
        >
          <td>{{ paciente }}</td>
          <td>{{ fecha }}</td>
          <td>{{ hora }}</td>
          <td>{{ motivo }}</td>
          <td>
            <button @click="$emit('eliminarConsulta', i)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: ["consultas"],
};
</script>

<style>
td,
th {
  padding: 10px;
}

.bg-red {
  background: red;
  color: white;
}
.bg-yellow {
  background: yellow;
}
.bg-green {
  background: greenyellow;
}
</style>

<template>
  <div>

    <form @submit.prevent="addRecord">
      <table>
        <tr>
          <td><label for="name">Nombre:</label></td>
          <td><input type="text" v-model="newRecord.name" required /></td>
          <td><label for="email">Correo:</label></td>
          <td><input type="email" v-model="newRecord.email" required /></td>
          <td><label for="age">Edad:</label></td>
          <td><input type="number" v-model="newRecord.age" required /></td>
          <td><button type="submit">Agregar</button></td>
        </tr>
      </table>
    </form>

    <table border="1">
      <thead>
        <tr>
          <th>Nombre</th>
          <th>Correo</th>
          <th>Edad</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(record, data) in records" :key="data">
          <td>{{ record.name }}</td>
          <td>{{ record.email }}</td>
          <td>{{ record.age }}</td>
          <td>
            <button class="delete-button" @click="deleteRecord(data)">Eliminar</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newRecord: {
        name: '',
        email: '',
        age: ''
      },
      records: []
    };
  },
  methods: {
    addRecord() {
      this.records.push({ ...this.newRecord }); 
      this.newRecord.name = ''; 
      this.newRecord.email = '';
      this.newRecord.age = '';
    },
    deleteRecord(index) {
      this.records.splice(index, 1); 
    }

  }
};
</script>

<style scoped>
table {
  width: 50%;
  margin: 20px auto;
  border-collapse: collapse;
}

table, th, td {
  border: 1px solid black;
}

th, td {
  padding: 10px;
  text-align: left;
}

button {
  background-color: #4CAF50;
  color: white;
  border: none;
  padding: 10px 20px;
  cursor: pointer;
}

.delete-button {
  background-color: #8B4513; 
  color: white;
}

button:hover {
  background-color: #45a049;
}
</style>
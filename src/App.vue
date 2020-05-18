<template>
  <div id="app">
    <table>
      <thead>
        <tr>
          <th colspan=10>
            Pool WSG
            <hr>
            Всего: {{ vms.length }}
          </th>
        </tr>
        <tr>
          <th>ID</th>
          <th>NAME</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(vm, index) in vms" :key="index">
          <td>{{vm.vmid}}</td>
          <td>{{vm.name}}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {  
    return {
      vms: [],
    }
  },
  async mounted(){
    const resp = await fetch("https://gitlab.tacid.kiev.ua:8006/api2/json/pools/WSG", {
      headers: {
        'Authorization': 'PVEAPIToken=root@pam!test-vue=813c7136-e79f-4718-8753-cc2757b705d1'
        },
    })
    const pool = await resp.json();
    console.log(pool);
    this.vms = pool.data.members;
  },
  components: {
  },
  methods: {
    doneTodo(index){
      this.todos.splice(index, 1);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
table {
  display: flexbox;
  margin-left: 20%;
  border: 1px solid #ccc;
  border-radius: 2px;
}
td, th {
  border: 1px solid #cec;
}

</style>

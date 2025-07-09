<template>
  <div v-if="data">
    <h4>(only applies to JWT-authenticated requests)</h4>
    <div v-for="(resource, index) in data" :key="index">
      <h3>{{resource.endpoint}}</h3>
      <table>
        <thead>
        <tr>
          <th>Method</th>
          <th>Scope</th>
        </tr>
        </thead>
        <tbody>
        <tr v-for="(scope, index) in resource.methods" :key="index">
          <td>{{index}}</td>
          <td v-html="scope"></td>
        </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      data: null
    }
  },
  mounted() {
    this.data = require('../../fixtures/scopes/scopes.json');
  }
}
</script>

<template>
  <div v-if="data">
    <h2>Required Scopes</h2>
    <p>Only applies to <a>JWT-authenticated requests</a>. See the <a href="/development/api/10_scopes.html">full list of endpoint scopes</a>.</p>
    <table>
      <thead>
        <tr>
          <th>Method</th>
          <th>Scope</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(scope, index) in data[resource].methods" :key="index">
          <td>{{index}}</td>
          <td v-html="scope"></td>
        </tr>
      </tbody>
    </table>
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
  },
  props: {
    resource: {
      type: String,
      required: true,
    }
  },
}
</script>

<template>
  <div>
    <tr>
      <td>
        <div class="row .col-xs-4">
        <input type="checkbox" v-model="good.isCheck"><img src="../assets/2b7a42c393cad4f2.jpg" style="height: 200px;width: 200px"/>
        </div>
      </td>
      <td >
        <div class="row .col-xs-8  col-xs-offset-6">
        <p style="margin-top: 100px;">{{good.message}}</p>
        <p>￥{{good.value}}元 </p>
        </div>
      </td>
    </tr>
  </div>
</template>

<script>
  export default {
    name: "item",
    props: ['good']
  }
</script>

<style scoped>

</style>

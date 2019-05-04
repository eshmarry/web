<template>
  <div>
    <tr style="font-size: 28px;font-weight: bold">
      <th colspan="2"><input type="checkbox" v-model="check" > {{item.storeName}}</th>
      <th style="width: 500px"><p style="margin-left: 200px">
        {{item.isFee==true?'已免运费':'未免运费'}}</p></th>
    </tr>

    <Row v-for="(good,index) in item.goods" :good="good" :key="index"/>

  </div>

</template>
<script>
  import Row from './Row.vue'
  import Pub from 'pubsub-js'
  export default {
    props: ['item','checkAll','count','handle','check'],
    name: 'ChoppingCart',
    components: {
      Row
    },
    computed: {

    }


  }
</script>


<style scoped>


</style>

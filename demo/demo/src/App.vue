<template>
  <div class="container">
    <div class="row">
      <div class=".col-xs-12 .col-xs-offset-4">
        <p style="font-size: 36px;font-weight: bold"> 购物车</p>
      </div>
    </div>
    <div class="row">
      <div class=".col-xs-10 .col-xs-offset-5">
        <ChoppingCart v-for="(item,index) in items" :item="item" :key="index"  :check="check"
                      :count="count"/>
      </div>
    </div>
    <div class="row col-xs-offset-10">
      <p style="font-size: 26px;font-weight: bold ;color: red">
        总计{{count}}
      </p>
    </div>
  </div>
</template>

<script>
  import ChoppingCart from './components/ChoppingCart'
  import Pub from 'pubsub-js'

  export default {
    name: 'App',
    components: {
      ChoppingCart
    },mounted() {

    }
    ,
    data() {
      return {
        name: '',
        items: [{
          isC: false,
          storeName: 'JD 自营店',
          isFee: true,
          goods: [{
            isCheck: false,
            name: 'surface',
            message: 'surface pro 6 二合一平白电脑',
            value: '16888',
            pho: '../assets/2b7a42c393cad4f2.jpg'
          },
            {
              name: 'surface',
              message: 'surface pro 6 二合一平白电脑',
              value: '16888',
              pho: '../assets/2b7a42c393cad4f2.jpg',
              isCheck: false
            }]
        },
          {
            isC: false,
            storeName: 'Microsoft',
            isFee: false,
            goods: [{
              name: 'surface',
              message: 'surface pro 6 二合一平白电脑',
              value: '16888',
              pho: '../assets/2b7a42c393cad4f2.jpg',
              isCheck: false
            }]
          },
        ]
      }
    },
    methods: {
      checkAll(is, name) {
        alert(is + "" + name)
        //if(this.items.storeName===name) {
        //this.items.goods.forEach(p => p.isCheck = is)
        //this.items.forEach(p => p.storeName === name ? p.goods.forEach(g => g.isCheck = is) : p.goods.forEach(g => g.isCheck = g.isCheck))
        //}
        let i = 0
        let len = this.items.length
        for (; i < len; i++) {
          if (this.items[i].storeName === name) {
            let j = 0
            let len1 = this.items[i].goods.length
            for (; j < len1; j++) {

              this.items[i].goods[j].isCheck = !is
              alert(this.items[i].goods[j].isCheck)
            }
          }
        }

      },
      accAdd(arg1, arg2) {
        let r1, r2, m;
        try {
          r1 = arg1.toString().split(".")[1].length
        } catch (e) {
          r1 = 0
        }
        ;
        try {
          r2 = arg2.toString().split(".")[1].length
        } catch (e) {
          r2 = 0
        }
        ;
        m = Math.pow(10, Math.max(r1, r2));
        return (arg1 * m + arg2 * m) / m;
      }

    }, computed: {

      count() {
        //return this.items.reduce((preTotal, item) => preTotal + (item.goods.isCheck?item.goods.value:0), 0)
        let i = 0
        let result = 0
        let len = this.items.length
        for (; i < len; i++) {
          let j = 0
          let len1 = this.items[i].goods.length
          for (; j < len1; j++) {
            if (this.items[i].goods[j].isCheck) {
              //result = result + this.items[i].goods[j].value
              result = this.accAdd(result, this.items[i].goods[j].value)
            }
          }
        }
        return result
      },
      handle() {
        let i = 0
        let len = this.items.length
        let j = 0
        let flag = true
        for (; i < len && flag; i++) {
          for (; j < this.items[i].goods.length && flag; j++) {
            if (!this.items[i].goods[j].isCheck)
              flag = false
          }
        }
        return flag
      },
      check: {
        set(value) {
          //let name = null

          //alert(v1)
          //alert(this.name)
          this.checkAll(value, name)
        }, get() {
          return this.handle
        }

      }

    }}
</script>

<style>

</style>

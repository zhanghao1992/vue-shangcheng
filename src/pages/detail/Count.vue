<template>
  <div class="right-box">
    <h3>{{data.name}}</h3>
    <p class="description">
      产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍
      产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍
      产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍产品介绍
    </p>
    <div>
      <form action="">
        <div class="form-group">
          <label for="">购买数量</label>
          <Number @changeNumber="changeNumberHandle"></Number>
        </div>
        <div class="form-group">
          <label for="">有效期</label>
          <span>{{detail.validity}}</span>
        </div>
        <div class="form-group">
          <label for="">单价</label>
          <span>{{detail.price }}元</span>
        </div>
        <div class="form-group">
          <label for="">地区</label>
          <Selects :list="cityList" @changeCity="changeCityHandle"></Selects>
        </div>
        <div class="form-group">
          <label for="">总价</label>
          <span>{{detail.price * num }}</span>
        </div>
      </form>
    </div>

    <a id="buy" @click="buyHandle" href="javascript:void (0);">立即购买</a>

    <base-dialog @clocseDialog="clossD" type="isBuyDialog"  v-show="isBuyDialog">
      <h3 slot="header">购物信息</h3>
      <div slot="content">
        <p style="text-indent: 2em;">暗杀计划单萨的痕</p>
      </div>
    </base-dialog>
  </div>
</template>

<script>
import BaseDialog from '../../components/BaseDialog'
import Number from '../../components/Number'
import Selects from '../../components/Select'

export default {
  name: 'hello',
  props: ['data'],
  data() {
    return {
      isBuyDialog: false,
      detail: {
        price: 20,
        validity: '半年',
      },
      cityList: [
        {
          name: '北京',
          code: 0
        },
        {
          name: '天津',
          code: 1
        },
        {
          name: '河北',
          code: 2
        },
        {
          name: '吉林',
          code: 3
        },
        {
          name: '辽宁',
          code: 4
        }
      ],
      num: 1,
      cityCode: 0
    }
  },
  components: {
    Number,
    Selects,
    BaseDialog
  },
  mounted() {
    this.cityCode = this.cityList[0].code
  },
  methods: {
    changeNumberHandle(num) {
      this.num = num
    },
    changeCityHandle(index) {
      this.cityCode = this.cityList[index].code
    },
    buyHandle () {
      this.isBuyDialog = true
    },
    clossD (type) {
        this[type] = false;
    }

  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.right-box {
  padding-bottom: 40px;
}
h3 {
  font-size: 14px;
  line-height: 30px;
  border-bottom: 1px solid tomato;
  padding-left: 10px;
}
.description {
  background-color: palegoldenrod;
  line-height: 20px;
  text-indent: 2em;
  padding: 10px;
}
form {
  margin-top: 20px;
  padding-left: 20px;
}
.form-group {
  margin: 5px 0;
  font-size: 14px;
}
.form-group label {
  display: inline-block;
  width: 80px;
  text-align: justify;
  text-align-last: justify;
  margin-right: 5px;
}
#buy {
  display: inline-block;
  width: 140px;
  font-size: 18px;
  border-radius: 6px;
  height: 30px;
  line-height: 30px;
  color: #fff;
  background: darkseagreen;
  text-align: center;
  margin-left: 100px;
}
</style>

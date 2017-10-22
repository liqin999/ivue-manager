<template>

  <div>
    <Row class="filterItem">
      <Col span="3" class="pr10">订单状态:</Col>
      <Col span="18" class="filterInfo">
        <a>全部</a>
        <a>待确认(10)</a>
        <a>待发货(10)</a>
        <a>已发货(10)</a>
        <a>已发货(10)</a>
        <a>已完成(10)</a>
        <a>已取消(10)</a>
        <a>异常单(10)</a>
        <a>退换货订单</a>
      </Col>
      <Col span="3" class="pr10 text-left" v-show="!isShowFilter" >
        <Button type="text" @click="fnshowFilter()">
          展开
          <Icon type="ios-arrow-down"></Icon>
        </Button>
      </Col>

      <Col span="3" class="pr10 text-left" v-show="isShowFilter">
        <Button type="text"  @click="fnshowFilter()">
        收缩
        <Icon type="ios-arrow-up"></Icon>
        </Button>
      </Col>
    </Row>

  <div v-show="isShowFilter">

    <Row class="filterItem">
      <Col span="3" class="pr10">送货地区:</Col>
      <Col span="21" class="filterInfo">
           <Cascader class="ml10" :data="city_data" v-model="address_value" style="width: 300px;"></Cascader>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">支付类型:</Col>
      <Col span="21" class="filterInfo">
      <a>全部</a>
      <a>在线支付</a>
      <a>货到付款</a>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">支付状态:</Col>
      <Col span="21" class="filterInfo">
      <a>全部</a>
      <a>待支付</a>
      <a>部分支付</a>
      <a>已支付</a>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">配送方式:</Col>
      <Col span="21" class="filterInfo">
      <a>货到付款了</a>
      <a>EMS</a>
      <a>顺丰快递</a>
      <a>自提</a>
      <a>宅急送</a>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">订购类型:</Col>
      <Col span="21" class="filterInfo">
      <a>全部</a>
      <a>积分换礼</a>
      <a>定金</a>
      <a>兑换</a>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">订购时间:</Col>
      <Col span="21" class="filterInfo">
      <a>全部</a>
      <a>本周</a>
      <a>本月</a>
      <a>本季度</a>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">是否有发票:</Col>
      <Col span="21" class="filterInfo">
      <a>全部</a>
      <a>是</a>
      <a>否</a>
      </Col>
    </Row>

    <Row class="filterItem">
      <Col span="3" class="pr10">电子面单打印状态:</Col>
      <Col span="21" class="filterInfo">
      <a>全部</a>
      <a>是</a>
      <a>否</a>
      </Col>
    </Row>
  </div>

    <VmTable title="产品管理"
             type="edit"
             :columns="dataColumns"
             :data="dataTable"
             v-on:add-ok="add"
             v-on:edit-ok="edit"
             v-on:delete-ok="deletefn">
    </VmTable>
  </div>

</template>

<script>
  import VmTable from '@/components/vm-table'
  import citys from '@/utils/citys'
  export default {
    mounted:function(){//引入地址插件
      //console.log(citys.regions)
    },
    name: 'EditableTable',
    components: {
      VmTable
    },
    methods: {
      fnshowFilter: function () {

        this.isShowFilter = !this.isShowFilter;
      },
      add: function (data) {//添加的时候 向开头增加
        this.dataTable.unshift(data)
      },
      edit: function (data) {
        this.dataTable.forEach(function (elem) {
          if (elem.id === data.id) {
            for (let i in data) {
              elem[i] = data[i]
            }
          }
        })
      },
      deletefn: function (data) {
        for (let i = 0; i < this.dataTable.length; i++) {
          for (let j = 0; j < data.length; j++) {
            if (this.dataTable[i].id === data[j].id) {
              this.dataTable.splice(i, 1)
            }
          }
        }
      }
    },
    data () {
      return {
        isShowFilter:false,
        address_value:"",
        city_data:citys.regions,
        dataColumns: [
          {
            id: '1',
            title: '缩略图',
            key: 'thumb'
          },
          {
            id: '2',
            title: '产品名称',
            key: 'proname'
          },
          {
            id: '3',
            title: '编号',
            key: 'id'
          },
          {
            id: '4',
            title: '所属分类',
            key: 'classify'
          },
          {
            id: '5',
            title: '零售价',
            key: 'price'
          },
          {
            id: '6',
            title: '发布日期',
            key: 'publishdate'
          }

        ],
        dataTable: [
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '111',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '222',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '333',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '444',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '555',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '666',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '777',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },
          {
            thumb: '65416s843154',
            proname: '65416s843154',
            id: '888',
            classify: '裤子',
            price: '120',
            publishdate: '2017-10-22',
          },

        ]
      }
    }
  }
</script>
<style scoped>
  /*公共样式*/
  .pr10{padding-right: 10px}
  .ml10{ margin-left: 10px;}
  .text-left{text-align: left}
  .text-right{text-align: right}

 /*当前页面样式*/
  .filterItem{;text-align:right;background-color: #fff;padding: 10px 0px}
  .filterInfo{text-align: left}
  .filterInfo a{padding: 0 10px}

</style>

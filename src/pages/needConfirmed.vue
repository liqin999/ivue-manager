<template>

  <div>
    <Row class="filterItem">
      <Col span="3" class="pr10">订单状态:</Col>
      <Col span="21" class="filterInfo">
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
    </Row>

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



    <VmTable title="Editable Table"
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
      add: function (data) {
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
        address_value:"",
        city_data:citys.regions,
        dataColumns: [
          {
            id: '20156541',
            title: '编号13123',
            key: 'id'
          },
          {
            id: '20156542',
            title: '姓名31231',
            key: 'name'
          },
          {
            id: '20156543',
            title: '年龄312313',
            key: 'age'
          },
          {
            id: '20156544',
            title: '地址3123',
            key: 'address'
          }
        ],
        dataTable: [
          {
            id: '65416s843154',
            name: '王小明',
            age: 18,
            address: '北京市朝阳区芍药居'
          },
          {
            id: '6541684q6534',
            name: '张小刚',
            age: 25,
            address: '北京市海淀区西二旗'
          },
          {
            id: '65416843f194',
            name: '李小红',
            age: 30,
            address: '上海市浦东新区世纪大道'
          },
          {
            id: '6541g6843150',
            name: '周小伟',
            age: 26,
            address: '深圳市南山区深南大道'
          },
          {
            id: '6541h6843150',
            name: '张小刚',
            age: 25,
            address: '北京市海淀区西二旗'
          },
          {
            id: '65416v843114',
            name: '李小红',
            age: 30,
            address: '上海市浦东新区世纪大道'
          },
          {
            id: '65416843g114',
            name: '周小伟',
            age: 26,
            address: '深圳市南山区深南大道'
          },
          {
            id: '254168431d54',
            name: '李小红',
            age: 30,
            address: '上海市浦东新区世纪大道'
          },
          {
            id: '65456843d154',
            name: '周小伟',
            age: 26,
            address: '深圳市南山区深南大道'
          },
          {
            id: '654168431d14',
            name: '张小刚',
            age: 25,
            address: '北京市海淀区西二旗'
          },
          {
            id: '65416343s154',
            name: '李小红',
            age: 30,
            address: '上海市浦东新区世纪大道'
          },
          {
            id: '65419843f154',
            name: '周小伟',
            age: 26,
            address: '深圳市南山区深南大道'
          }
        ]
      }
    }
  }
</script>
<style scoped>
  /*公共样式*/
  .pr10{padding-right: 10px}
  .ml10{
    margin-left: 10px;}
 /*当前页面样式*/
  .filterItem{;text-align:right;background-color: #fff;padding: 10px 0px}
  .filterInfo{text-align: left}
  .filterInfo a{padding: 0 10px}
</style>

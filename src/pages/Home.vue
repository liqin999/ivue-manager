<template>
  <div class="home">
    <Row class="header" type="flex" align="middle">
      <div class="logo">
        <img src="../assets/img/logo.png" height="30" alt="">
        <span>VUE</span>MANAGER <Tag>beta</Tag>
      </div>
      <VmMsgPush style="margin-left:20px" :data="msgPushData"></VmMsgPush>
      <Dropdown class="login-info" placement="bottom-end">
        <Button type="ghost">
            <img src="../assets/img/photo.jpg" height="30" alt="">Admin
            <Icon type="arrow-down-b"></Icon>
        </Button>
        <Dropdown-menu slot="list">
            <Dropdown-item divided><i class="fa fa-key"></i>Log out</Dropdown-item>
            <Dropdown-item divided><i class="fa fa-cog"></i>Setting</Dropdown-item>
        </Dropdown-menu>
      </Dropdown>
    </Row>
    <div class="sidebar">
      <Menu theme="dark" width="100%" class="menu">
          <Menu-item name="1">
              <router-link to="/">
                <i class="fa fa-dashboard"></i>
                Dashboard
              </router-link>
          </Menu-item>
          <Menu-item name="2">
              <router-link to="/widget">
                <i class="fa fa-cogs"></i>
                Widget
              </router-link>
          </Menu-item>
          <Menu-item name="3">
              <router-link to="/imagelist">
                <i class="fa fa-photo"></i>
                Image List
              </router-link>
          </Menu-item>
          <Menu-item name="4">
              <router-link to="/charts">
                <i class="fa fa-bar-chart"></i>
                Charts
              </router-link>
          </Menu-item>
          <Submenu name="5">
              <template slot="title">
                  <i class="fa fa-database"></i>
                  Data Table
              </template>
              <Menu-item name="5-1">
                <router-link to="/basic-table">
                  Basic Table
                </router-link>
              </Menu-item>
              <Menu-item name="5-2">
                <router-link to="/editable-table">
                  Editable Table
                </router-link>
              </Menu-item>
          </Submenu>
          <Submenu name="6">
              <template slot="title">
                  <i class="fa fa-file"></i>
                  Pages
              </template>
              <Menu-item name="6-1">
                <router-link to="/login">
                  Login
                </router-link>
              </Menu-item>
              <Menu-item name="6-2">
                <router-link to="/lockscreen">
                  Lockscreen
                </router-link>
              </Menu-item>
          </Submenu>

        <Submenu name="7">
          <template slot="title">
            <i class="fa fa-file"></i>
             订单管理
          </template>
          <Menu-item name="7-1">
            <router-link to="/need-confirmed">
              待确认
            </router-link>
          </Menu-item>
          <Menu-item name="7-2">
            <router-link to="/need-deliver">
              待发货
            </router-link>
          </Menu-item>
          <Menu-item name="7-3">
            <router-link to="/done-deliver">
              已发货
            </router-link>
          </Menu-item>
          <Menu-item name="7-4">
            <router-link to="/order-completed">
              已完成
            </router-link>
          </Menu-item>
          <Menu-item name="7-5">
            <router-link to="/order-canceled">
              已取消
            </router-link>
          </Menu-item>
          <Menu-item name="7-6">
            <router-link to="/order-abnormal">
              异常单
            </router-link>
          </Menu-item>
        </Submenu>



      </Menu>
    </div>
    <div class="main-content">
      <router-view></router-view>
      <p class="vm-author">vue-manager designed by <a href="https://github.com/luosijie" target="_blank">Jesse Luo</a></p>
    </div>
  </div>
  </div>
</template>
<script>
import VmMsgPush from '@/components/vm-msg-push.vue'
export default {
  name: 'home',
  components: {
    VmMsgPush
  },
  data () {
    return {
      msgPushData: [
        {
          image: require('@/assets/img/photo.jpg'),
          from: 'JesseLuo',
          time: '2017-1-8',
          message: 'I like your website very much!'
        },
        {
          image: require('@/assets/img/photo.jpg'),
          from: 'JesseLuo',
          time: '2017-1-8',
          message: 'I like your website very much!'
        },
        {
          image: require('@/assets/img/photo.jpg'),
          from: 'JesseLuo',
          time: '2017-1-8',
          message: 'I like your website very much!'
        },
        {
          image: require('@/assets/img/photo.jpg'),
          from: 'JesseLuo',
          time: '2017-1-8',
          message: 'I like your website very much!'
        },
        {
          image: require('@/assets/img/photo.jpg'),
          from: 'JesseLuo',
          time: '2017-1-8',
          message: 'I like your website very much!'
        }
      ]
    }
  }
}
</script>

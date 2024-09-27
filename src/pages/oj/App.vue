<template>
  <div>
    <NavBar></NavBar>
    <div class="content-app">
      <transition name="fadeInUp" mode="out-in">
        <router-view></router-view>
      </transition>
      <div class="footer">
        <p v-html="website.website_footer"></p>
        <p>Powered by <a href="https://www.scnu.edu.cn/">SCNUOJ</a>
          <span v-if="version">&nbsp; Version: {{ version }}</span>
        </p>
      </div>
    </div>
    <BackTop></BackTop>
  </div>
</template>

<script>
  import { mapActions, mapState } from 'vuex'
  import NavBar from '@oj/components/NavBar.vue'

  export default {
    name: 'app',
    components: {
      NavBar
    },
    data () {
      return {
        version: process.env.VERSION
      }
    },
    created () {
      try {
        document.body.removeChild(document.getElementById('app-loader'))
      } catch (e) {
      }
    },
    mounted () {
      this.getWebsiteConfig()
    },
    methods: {
      ...mapActions(['getWebsiteConfig', 'changeDomTitle'])
    },
    computed: {
      ...mapState(['website'])
    },
    watch: {
      'website' () {
        this.changeDomTitle()
      },
      '$route' () {
        this.changeDomTitle()
      }
    }
  }
</script>

<style lang="less">

  * {
    -webkit-box-sizing: border-box;
    -moz-box-sizing: border-box;
    box-sizing: border-box;
  }
  a {
    text-decoration: none;
    background-color: transparent;
    &:active, &:hover {
      outline-width: 0;
    }
  }
 
  .content-app{
  background: #34312f;
  }
  .content-app .ivu-card{
    background-image: linear-gradient(to bottom,#595858,#3c3937);  
;
  color: #ccab6c;
box-shadow: #e6c079 2px;}
  //翻页按钮
  .content-app .page .ivu-page .ivu-page-item {
color: #000;
border: none;
background-image: linear-gradient(to right,#ccab6c,#b38922);  
}
.content-app .page .ivu-page .ivu-page-item :hover{
color: #000;
border: 1px solid #B38922;
}
.content-app .page .ivu-page .ivu-page-item-active
{
  background-image: linear-gradient(to right,#fedea0,#ccab6c);  
  color: #000;
  border: 1px solid #000;
}
//页数显示
.page .ivu-select-selection
{color: #34312f;
  border: none;
  background-image: linear-gradient(to right,#ccab6c,#b38922);  
}
.page .ivu-select-selection i
{color: #34312f;
  background: #666;
}
.page .ivu-select-selection:hover {
  border: 1px solid #B38922;
background-color: #000;
color: #34312f;
}
.page .ivu-select-item-selected {
  background: #000000;
  color: #B38922;
}
.ivu-select-selected-value{
  border: #ccab6c 1px solid;
  box-shadow: #ccab6c 1px;
}
.ivu-select-dropdown
{
  // background: #B38922;
  background-image: linear-gradient(to right,#CCAB6C,#B38922);  
}
.ivu-select-item
{
  color: #fff;
}
.ivu-select-item:hover
{background: #2c2c2c;
  color: #CCAB6C;
}
// 难度选择部分翻页框
.filter .ivu-select-dropdown li{
  color: #34312f;
}
.filter .ivu-select-dropdown li:hover{
  background: #1f1f1f;
  color: #B38922;
}
  @media screen and (max-width: 1200px) {
  .content-app {
    margin-top: 160px;
    padding: 0 2%;
  }
 
}
// 前后翻页按钮
.page .ivu-page-prev,
.page .ivu-page-next {
  background-image: linear-gradient(to right,#ccab6c,#b38922); 
color: #34312f; 
border: none;}
// 状态下的表格
.ivu-table-header .ivu-table-column-center {
 color: #ccab6c;
// background-color: #34312f;
  // background-image: linear-gradient(to bottom,#ccab6c,#b38922);  
}
// 状态栏内字体效果，似乎有点丑，先注释掉
/*.ivu-table-header .ivu-table-column-center span
{
  display: block;
  width: 36px;
  height: 24px;
  line-height: 24px;
  border-radius: 5px;
  background-image: linear-gradient(to bottom,#ccab6c,#b38922);  
}*/
.ivu-table-tip td
{
  color: #ccab6c;
  // background-color: #34312f;
  // background-image: linear-gradient(to bottom,#595858,#3c3937);  
}
// 问题列表表格
.ivu-table-cell span
{
  // background: #34312f;
  color: #ccab6c;
}
// 标签
.tag-btn
{
  color: #CCAB6C;
}
// 右上角用户管理
.drop-menu-title
{
  color: #ccab6c;
}
.ivu-dropdown-item-divided:before
{
  background:none;
}
// 用户管理
// 左上角logo
.logo
{
color: #ccab6c;
}
// 比赛页面
.contest-main p a
{
color: #CCAB6C;
}

.content-app.ivu-card-body ul li i
{
  color: #ccab6c;
}
.ivu-card-body ul li
{
  color: #ccab6c;
}
.ivu-card-body ul li:hover
{background: #000;
  color: #fedea0;
  border-left:1px solid #fedea0;
}
// 我的设置
 .ivu-card-bordered .flex-container
 {
 background: #fff;
}
.ivu-card-bordered .flex-container .ivu-form-item-label
{
  color: #CCAB6C;
}
.ivu-card-bordered .flex-container .menu .ivu-menu-item
{
  color: #ccab6c;
}
// 我的主页
.ivu-card-body div .flex-container
{
  background: none;;
}
.ivu-btn-ghost
{
  color: #ccab6c;
}
// 题目页面选项框
.ivu-col-span-12 .adjust .ivu-select-dropdown ul li
{
  color: #34312f;
}
.ivu-col-span-12 .adjust .ivu-select-dropdown ul li:hover
{
  color: #ccab6c;
}
// 题目页面选项框
.ivu-col-span-12 .adjust .ivu-select-dropdown ul .ivu-select-item-selected
{ 
  background: #000;
}
.ivu-btn-circle
{border: none;
  background-image: linear-gradient(to right,#ccab6c,#b38922);  
  color: #34312f;
}
.ivu-btn-circle:hover
 {
  // border: 1px solid #000;
border: none;
  background-image: linear-gradient(to right,#fedea0,#b38922);  
  color: #34312f;
}
// 我的设置下拉语言设置框
.ivu-form-item-content .ivu-select-dropdown-list .ivu-select-item
{
  color: #34312f;
}
.ivu-form-item-content .ivu-select-dropdown-list .ivu-select-item:hover
{
  color: #fedea0
}
.ivu-form-itemm-content .ivu-select-dropdown-list .ivu-select-item-focus
{
  background-image: linear-gradient(to right,#fedea0,#b38922);  
  color: #34312f;
}
@media screen and (min-width: 1200px) {
  .content-app {
    margin-top: 80px;
    padding: 0 2%;
  }
}

  .footer {
    margin-top: 20px;
    margin-bottom: 10px;
    text-align: center;
    font-size: small;
    // 更改字体颜色
    color: #ccab6c;
    a{
      color: #fff;
    }
    // 排名页小图标
   canvas
   {
    color: #ccab6c;
   }
  //  排名页数据视图
  .echarts
  {
    background: #34312f;
    color: #ccab6c;
  }
  .menu ul {
    background: #000;
  }
  }

  .fadeInUp-enter-active {
    animation: fadeInUp .8s;
  }


</style>

<template>
  <Card :padding="padding" :shadow="shadow" :dis-hover="disHover" :bordered="bordered">
    <div slot="title" class="panel-title">
      <slot name="title"></slot>
    </div>
    <div slot="extra" class="panel-extra">
      <slot name="extra"></slot>
    </div>
    <div class="panel-body">
      <slot></slot>
    </div>
  </Card>
</template>

<script>
  export default {
    name: 'Panel',
    props: {
      shadow: {
        required: false,
        type: Boolean,
        default: false
      },
      padding: {
        required: false,
        type: Number,
        default: 0
      },
      disHover: {
        required: false,
        type: Boolean,
        default: false
      },
      bordered: {
        required: false,
        type: Boolean,
        default: true
      }
    }
  }
</script>

<style lang="less">
  @import (reference) '../../../styles/common.less';

  .panel-title {
    .section-title;
    padding: 5px 15px;
  }

  .panel-extra {
    line-height: 40px;
    .ivu-input-icon {
      line-height: 40px;
    }
    ul.filter {
      > li {
        display: inline-block;
        padding: 0 10px;
      }
    }
    // 刷新按钮
    .ivu-btn-info
    {margin: 1px;
      background-image: linear-gradient(to right,#CCAB6C,#B38922);  
      color: #3b3a33;
      font-weight: 700;
      border:1px solid #3b3a33;
    }
    .ivu-btn-info:hover
    {transition: all 1s;
      background-image: linear-gradient(to right,#fedea0,#c2a166);  

      color: #3b3a33;
      font-weight: 700;
      border:1px solid #000000;
      box-shadow: #B38922 0px 0px 2px 0px;
    }
// 按钮开关
.ivu-switch-checked
{
  background-image: linear-gradient(to right,#CCAB6C,#B38922);  
  color: #3b3a33;
  border: 1px solid #b2b2aa;
}
// 开关内文字
.ivu-switch-inner
{
  color: #3b3a33;
  font-weight: 700;
}
// 搜索框
.ivu-input
{
  background-image: linear-gradient(to right,#CCAB6C,#B38922);  
  border: none;
  color: #34312f;
}
.ivu-input:hover
{
  background-image: linear-gradient(to right,#fedea0,#c2a166);  

}
.ivu-input::placeholder
{
  color: #34312f;
}
.iuv-input-icon
{
  color: #34312f;
}
  }
  .panel-body {
    word-break: break-all;
    word-wrap: break-word;
    // 底部页面跳转
    // 字体active状态怎么不是黑色
    .ivu-page-item:hover
    {
      color: #3b3a33;
      border:2px solid #B38922;
    }
    .ivu-page-item a:hover
    {color: #3b3a33;
    }
  .ivu-page-item-active
  { color: #000000;
    background-image: linear-gradient(to bottom,#ccab6c,#b38922);  
    border:1px solid #3b3a33;
  }
  .ivu-table-header th
  {
    background: #34312f;
  }
 
  // 标签下的选择按钮
  #pick-one
  {
    background-image: linear-gradient(to right,#ccab6c,#b38922);  
    color: #000000;
  }
  #pick-one:hover
  {
    background-image: linear-gradient(to right,#fedea0,#ccab6c);  
    color: #000000;
  }
  // ACM排名页面
  canvas
  {
    background:#fff;
  }
  // 比赛链接
  #contest-card #contest-list > li .contest-main .title a.entry[data-v-15291866]
  {
    color: #CCAB6C;
  }
  }
</style>

<template>
  <div class="part-one">
    <el-row>
      <el-col :xs="24" :sm="12" :md="12" :lg="24" class='flex'>
        <img class="part-one-image" :src="headImage" alt="头像">
      </el-col>
      <el-col :xs="24" :sm="12" :md="12" :lg="24">
        <p>姓&emsp;&emsp;名：张卓如</p>
        <p>学&emsp;&emsp;历：本科</p>
        <p>工作年限：1 年</p>
        <p>年&emsp;&emsp;龄：23</p>
        <p>联系电话：18818881888</p>
        <p>电子邮箱：2276839311@qq.com</p>
        <p>博&emsp;&emsp;客：<a href="http://jsliang.top" target="_blank">jsliang.top</a></p>
        <p>掘&emsp;&emsp;金：<a href="https://juejin.im/user/584613ba128fe10058b3cf68" target="_blank">jsliang</a></p>
        <p>GitHub：<a href="https://github.com/LiangJunrong" target="_blank">LiangJunrong</a></p>
      </el-col>
    </el-row>
    
    
  </div>
</template>

<script>
export default {
  name: "partOne",
  data() {
    return {
      headImage: require('../assets/img/head_image.png')
    }
  }
};
</script>

<style scoped>
a {
  color: deepskyblue;
}
a:hover {
  color: rgb(118, 190, 248);
}
p {
  line-height: 30px;
}
.part-one {
  width: 100%;
  max-height: 500px;
  min-height: 350px;
  border: 40px solid transparent;
  border-image: url("../assets/img/border_image.png") 30 30 stretch;
  background: #18202d;
  padding-left: 10px;
}
.flex{
  display: -webkit-flex;
  display: -moz-flex;
  display: -ms-flex;
  display: -o-flex;
  display: flex;
  justify-content:center;
}
.part-one-image {
  width: 150px;
  height: 150px;
}
</style>
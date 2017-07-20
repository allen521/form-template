<template>
    <div class="hello">
        <!--<h2>{{msg}}</h2>-->
        <div class="content">
            <h4 class="text-center">v-model绑定了具体值</h4>
            <training-ipt v-model="test1"  placeholder='名称'></training-ipt>
            <br>
            <h4 class="text-center">v-model绑定的是空</h4>
            <training-ipt v-model="test2"  placeholder='Name'></training-ipt>
            <br>
            <h4 class="text-center">v-model绑定了具体值 并设置了required</h4>
            <training-ipt v-model="test3"  placeholder='Email' :required='true'></training-ipt>
            <br>
        </div>
    </div>
</template>

<script>
import trainingIpt from '../components/input.vue'
export default {
  components:{
    trainingIpt,
  },
  data () {
    return {
      //msg: '欢迎查看由 Allen 定制化input组件',
      test1:"关关雎鸠，在河之洲；窈窕淑女，君子好逑。",
      test2:"",
	  test3:"510700429@qq.com",
	  Name:'哈哈',
	  Email:'510700429@qq.com'
    }
  }
}
</script>

<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.login-msg {
	padding: 50px;
	text-align: center;
}
.msg {
	padding: 50px;
	text-align: center;
	font-size: 20px;
	color: red;
}
.content{padding:50px 30%;}
.text-center{text-align: center}
h4{margin:10px;}
</style>

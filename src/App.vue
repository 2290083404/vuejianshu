<template>
  <div>
  	<Row>
  		<Col span="24">
  			<div class="logo">
  				<img src="./assets/logo.png">
  			</div>
  		</Col>
  	</Row>
  	<Row>
  		<Col span="8" >
  		</Col>
  		<Col span="8" offset="8">
  			<div id="app">
		    	<template>
				    <div class="hello">
				      <h4 class="title">
				        <div class="normal-title">
				        	
				          <router-link v-bind:class="{active:loginclass.isactive,disactive:loginclass.isdisactive}" to="/login" @click.native="dochangelogin">登录</router-link>
				          <b>·</b>
				          <router-link v-bind:class="{active:registerclass.isactive,disactive:registerclass.isdisactive}" to="/register" @click.native="dochangeregister">注册</router-link>
				        </div>
				      </h4>
				      <router-view></router-view>
				    </div>
				</template>
		  	</div>
  		</Col>
  		<Col span="8"></Col>
  	</Row>
  </div>
</template>

<script>

export default {
  name: 'app',
  data () {
    return {
      message: '12412',
      loginclass: {
        isactive: true,
        isdisactive: false
      },
      registerclass: {
        isactive: false,
        isdisactive: true
      }
    }
  },
  methods: {
    dochangelogin: function (event) {
      // `this` 在方法里指当前 Vue 实例
      this.loginclass.isactive = true
      this.loginclass.isdisactive = false
      this.registerclass.isactive = false
      this.registerclass.isdisactive = true
    },
    dochangeregister: function (event) {
      this.loginclass.isactive = false
      this.loginclass.isdisactive = true
      this.registerclass.isactive = true
      this.registerclass.isdisactive = false
    }
  }
}
</script>

<style>
#app{
	background-color: #fff;
	width: 400px;
    margin: 60px auto 0;
    padding: 50px 50px 30px;
    background-color: #fff;
    border-radius: 4px;
    box-shadow: 0 0 8px rgba(0,0,0,.1);
    vertical-align: middle;
    display: inline-block;
}
a:hover{
	
}
.logo{
	position: absolute;
    top: 56px;
    margin-left: 50px;

}
.logo>img{
	width: 100px;
}
.title{
  font-family: -apple-system,SF UI Display,Arial,PingFang SC,Hiragino Sans GB,Microsoft YaHei,WenQuanYi Micro Hei,sans-serif;
  margin: 0 auto 50px;
  padding: 10px;
  font-weight: 400;
  color: #969696;
  text-align: center;
}
.active{
  font-weight: 700;
  color: #ea6f5a;
  border-bottom: 2px solid #ea6f5a;
}
.disactive{
  color: #969696;
}
.title a{
  padding: 10px;
}
h4{
  line-height: 1.1;
  font-size: 18px;
}
.more-sign{
  margin-top: 30px;
  
}
:after, :before {
    box-sizing: border-box;
}

h6{
    font-family: inherit;
    font-weight: 500;
    line-height: 1.1;
    text-align: center;
}
.more-sign h6 {
    position: relative;
    margin: 0 0 20px;
    font-size: 12px;
    color: #b5b5b5;
}

h6:after,  .more-sign h6:before {
    content: "";
    border-top: 1px solid #b5b5b5;
    display: block;
    position: absolute;
    width: 60px;
    top: 5px;
}
h6:before {
    left: 30px;
}
h6:after {
    right: 30px;
}
.more-sign h6 {
    position: relative;
    margin: 0 0 20px;
    font-size: 12px;
    color: #b5b5b5;
}
</style>

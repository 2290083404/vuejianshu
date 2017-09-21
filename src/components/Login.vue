<template>
    <div class="loginForm">
      <Row>
        <Col span="24">
          <div>
            <Form :model="formItem" :label-width="50">
              <FormItem label="用户名">
                  <Input v-model="username" icon="person" placeholder="请输入用户名称"></Input>
              </FormItem>
              <FormItem label="密                        码">
                <Input v-model="password" icon="locked" type="password" placeholder="请输入用户密码"></Input>
              </FormItem>
              <br>
          </Form>
            
          </div>
        </Col>
        <Col span="24">
          <Button type="primary" long shape="circle" size="large" :loading="loading" @click="checklogin" style="background-color:#187cb7">登陆</Button>
            <div class="more-sign">
              <h6>社交帐号登录</h6>
              <div style="margin-left:20px">
                <Col span="6"><Avatar icon="social-twitter" size="large" style="background-color: #87d068"/></Col>
                <Col span="6"><Avatar icon="social-octocat" size="large" style="background-color: red"/></Col>
                <Col span="6"><Avatar icon="social-github" size="large" style="background-color: rgb(24, 124, 183)"/></Col>
                <Col span="6"><Avatar size="large">其他</Avatar></Col>
              </div>
            </div>
        </Col>
      </Row>
    </div>
</template>
<script>
export default {
  name: 'loginForm',
  data () {
    return {
      loading: false,
      username: '',
      password: '',
      checkstate: {
        usernamelength: false,
        passwordlength: false
      },
      jstitle: {
        successtitle: 'js验证通过',
        errortitle: 'js验证不通过'
      },
      jsdes: {
        success: '开始验证用户名和密码是否匹配',
        error: '用户名或者密码长度不对'
      },
      mysqltitle: {
        successtitle: '数据库验证通过',
        errortitle: '数据库验证不通过'
      },
      mysqldes: {
        successdes: '开始验证用户名和密码是否匹配',
        errordes: '用户名或者密码长度不对'
      }
    }
  },
  methods: {
    checklogin () {
      this.$Notice.destroy()
      if (this.username.length > 6 && this.username.length < 12) {
        this.checkstate.usernamelength = true
      }
      if (this.password.length > 6 && this.password.length < 12) {
        this.checkstate.passwordlength = true
      }
      if (this.checkstate.usernamelength && this.checkstate.passwordlength) {
        this.loading = true
        this.$Notice.success({
          title: this.jstitle.successtitle,
          desc: this.jsdes.success
        })
        var self = this
        this.$ajax.get('http://localhost:3000', {
          params: {
            username: this.username,
            password: this.password
          }
        })
        .then(function (res) {
          self.loading = false
          if (res.data.code === 200) {
            self.$Notice.success({
              title: self.mysqltitle.successtitle,
              desc: self.mysqldes.successdes
            })
          } else {
            self.$Notice.error({
              title: self.mysqltitle.errortitle,
              desc: self.mysqldes.errordes
            })
          }
        }).catch(function (res) {
          console.log(res)
        })
      } else {
        this.$Notice.error({
          title: this.jstitle.errortitle,
          desc: this.jsdes.error
        })
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    
</style>
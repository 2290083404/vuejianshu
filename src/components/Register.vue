<template>
    <Row>
        <Col span="24">
          <div>
            <Form :model="formItem" :label-width="50">
              <FormItem label="用户名">
                  <Input v-model="username" icon="person" type="text" placeholder="请输入用户名称"></Input>
              </FormItem>
              <FormItem label="密                        码">
                <Input v-model="password" icon="locked" type="password" placeholder="请输入用户密码"></Input>
              </FormItem>
              <FormItem label="邮                        箱">
                <Input v-model="email" icon="email" type="text" placeholder="请输入邮箱"></Input>
              </FormItem>
              <br>
          </Form>
            
          </div>
        </Col>
        <Col span="24">
          <Button type="primary" long shape="circle" size="large" style="background-color:#187cb7">注册</Button>
            <div class="more-sign">
              <h6>社交帐号注册</h6>
              <div style="margin-left:20px">
                <Col span="6"><Avatar icon="social-twitter" size="large" style="background-color: #87d068"/></Col>
                <Col span="6"><Avatar icon="social-octocat" size="large" style="background-color: red"/></Col>
                <Col span="6"><Avatar icon="social-github" size="large" style="background-color: rgb(24, 124, 183)"/></Col>
                <Col span="6"><Avatar size="large">其他</Avatar></Col>
              </div>
            </div>
        </Col>
      </Row>
</template>
<script>
export default {
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    
</style>
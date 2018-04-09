<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div class="btn">
      <a href="javascript:;" @click="createMenu()">创建菜单</a>
    </div>
    <div class="btn">
      <a href="javascript:;" @click="jumpToOauth2()">微信授权</a>
    </div>
    <div class="btn">
      <a href="javascript:;" @click="insertData()">插入数据</a>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Hope Project'
    }
  },
  methods:{
    createMenu() {
      axios.get('/wx/createVueMenu').then((res)=>{
        if (res.data.msg === 'ok') {
          alert('创建成功');
        } else {
          alert('创建失败');
        }
      })
    },
    jumpToOauth2() {
      this.$router.push({
        path:'/test',
      });
    },
    insertData() {
      axios.get('/mysql/insertData').then((res) => {
        if (res.data.status === 200) {
          alert('插入成功');
        } else {
          alert(res.data.msg);
        }
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
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
btn {
  height: 38px;
  line-height: 38px;
  border: 2px solid #009de6;
  background: #009de6;
  color: #fff;
  font-size: 18px;
  text-align: center;
  border-width: 1px;
}
</style>

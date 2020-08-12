<template>
  <div id="app">
    <label>
      <!-- 切换为横向 -->
      <input type="checkbox" v-model="landscape" value="1">
    </label>
    <TreeChart :json="data" :class="{landscape: landscape.length}" @click-node="clickNode" />
    
  </div>
</template>

<script>
import TreeChart from "@/components/TreeChart";

export default {
  name: 'app',
  components: {
    TreeChart
  },
  data() {
    return {
      landscape: [],
      data: {
        name: 'root',
        title:"发起申请",
        body:"发起人",
        image_url: "https://static.refined-x.com/static/avatar.jpg",
        class: ["rootNode"],
        children: [
          {
            name: 'children1',
            title:"分支1",
            body:"请假时长<=8小时",
            image_url: "https://static.refined-x.com/static/avatar.jpg"
          },
          {
            name: 'children2',
            title:"分支2",
            body:"请假时长很长",
            image_url: "https://static.refined-x.com/static/avatar.jpg",
            // mate: [
            //   {
            //     name: 'mate',
            //     image_url: "https://static.refined-x.com/static/avatar.jpg"
            //   }
            // ],
            children: [
              {
                name: 'grandchild',
                title:"分支x",
                body:"请假时长", 
                image_url: "https://static.refined-x.com/static/avatar.jpg"
              },
              {
                name: 'grandchild2',
                title:"分支9",
                body:"xxx",
                image_url: "https://static.refined-x.com/static/avatar.jpg"
              },
              {
                name: 'grandchild3',
                title:"分支yy",
                body:"999",
                image_url: "https://static.refined-x.com/static/avatar.jpg"
              }
            ]
          }
        ]
      }
    }
  },
  methods: {
    clickNode: function(node){
      // eslint-disable-next-line
      // const length = children.length ? children.length : 
      console.log(node,'node')
      let children;
      if(node.children) {
        children = node.children
      }else {
        children = [];
        this.$set(node,'children',children)
      }
      console.log(children,'children')
      const key = children&&children.length ? children.length : 0;
      // debugger
      console.log(key,'key')
      const value = {
        name:"add",
        title:"新增加",
        body:"success"
      }
      this.$set(children,key,{
        name:"add",
        title:"新增加",
        body:"success"
      })
      console.log(children,'children')
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app .avat{border-width:2px;}
#app .name{font-weight:700;}
#app .rootNode .name{
  color: red;
}

.foot {
    position: fixed;
    left: 0;
    bottom: 0;
    width: 100%;
    background: #333;
    padding: 24px;
    overflow: hidden;
    color: #999;
    font-size: 14px;
    text-align: center;
}
.foot a{color:#fff;margin:0 .5em}
</style>

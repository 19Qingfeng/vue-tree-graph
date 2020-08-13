<template>
    <div id="app">
        <TreeChart
            :json="data"
            :level="getTreeDepth(data)"
            :id="getMax(data)"
            :class="{landscape: landscape.length}"
            @click-node="clickNode"
            :height="174"
        />
    </div>
</template>

<script>
import TreeChart from "@/components/TreeChart";

export default {
  name: "app",
  components: {
    TreeChart
  },
  data() {
    return {
      landscape: [],
      mockId: 10000,
      data: {
        name: "root",
        id: "1",
        title: "发起申请",
        body: "发起人",
        level: 1,
        image_url: "https://static.refined-x.com/static/avatar.jpg",
        class: ["rootNode"],
        node: null,
        children: [
          {
            name: "children1",
            id: "2",
            title: "分支1",
            level: 2,
            body: "请假时长<=8小时",
            image_url: "https://static.refined-x.com/static/avatar.jpg",
          },
          {
            name: "children2",
            title: "分支2",
            id: "3",
            level: 2,
            body: "请假时长很长",
            image_url: "https://static.refined-x.com/static/avatar.jpg",
            // mate: [
            //   {
            //     name: 'mate',
            //     image_url: "https://static.refined-x.com/static/avatar.jpg"
            //   }
            // ],
            children: [
              {
                name: "grandchild",
                title: "分支x",
                id: 4,
                level: 3,
                body: "请假时长",
                image_url: "https://static.refined-x.com/static/avatar.jpg",
              },
              {
                name: "grandchild2",
                title: "分支9",
                level: 3,
                id: 5,
                body: "xxx",
                image_url: "https://static.refined-x.com/static/avatar.jpg",
              },
              {
                name: "grandchild3",
                level: 3,
                id: 6,
                title: "分支yy",
                body: "999",
                image_url: "https://static.refined-x.com/static/avatar.jpg",
              },
            ],
          },
        ],
      },
    };
  },
  methods: {
    // 获得最后节点 取消border的id
    getMax(data) {
      let node = null;
      function each(data) {
        const length = data.length - 1;
        for (let [key, value] of data.entries()) {
          if (key === length) {
            if (value.children && value.children.length) {
              // 继续调用
              each(value.children);
            } else {
              node = value;
            }
          }
        }
      }
      each(data.children);
      return node.id;
    },
    getTreeDepth(treeData) {
      let max = 0;
      treeData = [treeData];
      function each(data, floor) {
        data.forEach((node) => {
          if (floor > max) {
            max = floor;
          }
          if (node.children && node.children.length > 0) {
            each(node.children, floor + 1);
          }
        });
      }
      each(treeData, 1);
      return max;
    },
    clickNode(node) {
      let children;
      if (node.children) {
        children = node.children;
      } else {
        children = [];
        this.$set(node, "children", children);
      }
      const key = children && children.length ? children.length : 0;
      this.$set(children, key, {
        name: "add",
        title: "新增加",
        body: "success",
        level: node.level + 1,
        id: this.mockId--,
      });
    },
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app .avat {
  border-width: 2px;
}
#app .name {
  font-weight: 700;
}
#app .rootNode .name {
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
.foot a {
  color: #fff;
  margin: 0 0.5em;
}
</style>

# vue-tree-graph
> 基于vue和table布局实现graph动态组织结构图。

### Example:
```
// 增加id唯一属性 每个节点id必须唯一
{
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
      }
```

### 等待完善 ing...
### 强烈耦合业务，增加底部收尾（计算高度方式）。更改数据结构，等待优化ing

                name: "grandchild",地步
                name: "grandchild",

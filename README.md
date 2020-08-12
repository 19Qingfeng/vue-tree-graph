# vue-tree-graph
> 基于vue和table布局实现graph动态组织结构图。

### Example:
```
 {
        name: 'root',
        title:"发起申请",
        body:"发起人",
        class: ["rootNode"],
        children: [
          {
            name: 'children1',
            title:"分支1",
            body:"请假时长<=8小时",
          },
          {
            name: 'children2',
            title:"分支2",
            body:"请假时长很长",
            children: [
              {
                name: 'grandchild',
                title:"分支x",
                body:"请假时长",
              },
              {
                name: 'grandchild2',
                title:"分支9",
                body:"xxx"
              },
              {
                name: 'grandchild3',
                title:"分支yy",
                body:"999"
              }
            ]
          }
        ]
      }
```

### 等待完善 ing...

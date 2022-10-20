<template>
  <div class="home">
    <el-table :data="tableData" style="width: 100%" row-key="id" border default-expand-all :tree-props="{children: 'children', hasChildren: 'hasChildren'}">
      <el-table-column label="菜单" width="180">
        <template slot-scope="scope">
          <div v-if="!scope.row.flag">{{scope.row.date}}</div>
          <el-input v-else v-model="scope.row.date"></el-input>
        </template>
      </el-table-column>
      <el-table-column prop="name" label="url" width="180"> </el-table-column>
      <el-table-column prop="address" label="操作">
        <template slot-scope="scope">
          <el-button type="primary" @click="scope.row.flag = !scope.row.flag"><span v-if="!scope.row.flag">修改</span><span v-else>保存</span></el-button>
          <el-button type="primary" @click="tableData.push({
         id: Date.now(),
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          flag: false,
        })">添加一级</el-button>
          <el-button type="primary" @click="scope.row.children.push({
         id: Date.now(),
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          flag: false,
        })">添加二级菜单</el-button>
          <el-button @click.native.prevent="deleteRow(scope.$index, tableData)" type="danger">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: "HomeView",
  data() {
    return {
      tableData:  [{
          id: 1,
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          flag: false,
          children: []
        }, {
          id: 2,
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1517 弄',
          flag: false,
          children: []
        }, {
          id: 3,
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1519 弄',
          flag: false,
          children: [{
              id: 31,
              date: '2016-05-01',
              name: '王小虎',
              address: '上海市普陀区金沙江路 1519 弄',
          flag: false,
            }, {
              id: 32,
              date: '2016-05-01',
              name: '王小虎',
              address: '上海市普陀区金沙江路 1519 弄',
          flag: false,
          }]
        }, {
          id: 4,
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1516 弄',
          flag: false,
          children: []
        }]
    };
  },
  components: {
    // HelloWorld
  },
  methods: {
    deleteRow(index, rows) {
      console.log(index)
        rows.splice(index, 1);
      }
    },
};
</script>

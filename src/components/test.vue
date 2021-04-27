<template>
    <div class="page">
        <div class="left">
            <div v-for="(item, index) in list" :key="index">
              <el-checkbox v-model="item.choose" @change="changeClick(item)"></el-checkbox>
              <span>{{item.name}}</span>
            </div>
        </div>
        <div class="right">
            <div v-for="(i, index) in rightList" :key="index" class="div-list">
                <el-table
                    :ref="`multipleTable${i.id}`"
                    :data="i.table"
                    tooltip-effect="dark"
                    style="width: 100%"
                    @selection-change="handleSelectionChange">
                    <el-table-column
                    type="selection"
                    width="55">
                    </el-table-column>
                    <el-table-column
                    label="日期"
                    width="120">
                    <template slot-scope="scope">{{ scope.row.date }}</template>
                    </el-table-column>
                    <el-table-column
                    prop="name"
                    label="姓名"
                    width="120">
                    </el-table-column>
                    <el-table-column
                    prop="address"
                    label="地址"
                    show-overflow-tooltip>
                    </el-table-column>
                </el-table>
            </div>
        </div>
    </div>
</template>
<script>
export default{
  name: 'test',
  data () {
    return {
      list: [{
          name: 'yy',
          choose: false,
          id: '1',
          table: []
      },{
         name: 'qq',
         choose: false,
         id: '2',
         table: []
      },{
         name: 'ss',
         choose: false,
         id: '3',
         table: []
      }],
        tableData: [{
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }],
        tableData1: [{
          date: '2016-03-03',
          name: '王小',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-03-02',
          name: '王小',
          address: '上海市普陀区金沙江路 1518 弄'
        }],
        tableData2: [{
          date: '2016-02-03',
          name: '王虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-02-02',
          name: '王虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }],       

    }
  },
  methods:{
      changeClick(item) {
          let obj = {
              '1': this.tableData,
              '2': this.tableData1,
              '3': this.tableData2
          }
          item.table = obj[item.id]
          this.rightList.forEach((i)=>{
              this.$nextTick(()=>{
                if(item.id === i.id){
                    this.$refs[`multipleTable${i.id}`][0].toggleAllSelection()
                } 
              })
              
          })
      },
      handleSelectionChange() {

      }
  },
  computed:{
      rightList(){
          return this.list.filter((item)=>{
              return item.choose
          })
      }
  },
  watch:{  
  }
}
</script>
<style scoped>
.page{
    display: flex;
}
.left {
    width: 300px;
    height: 100%;
}
.right {
    width: calc(100% - 300px);
    height: 100%;
}
.div-list{
    margin-bottom: 20px;
}
</style>


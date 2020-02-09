<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div style="padding-left:20px; padding-right: 20px;">
      <el-table
        :data="tableData"
        style="width: 100%;"
        v-on:sort-change="sortChange">
        <el-table-column
          type="selection"
          width="55">
        </el-table-column>
        <el-table-column
          prop="title"
          label="Exercise"
          sortable="custom"
          style="width: 80%">
        </el-table-column>
        <el-table-column
          prop="vessel_type"
          label="Vesel type"
          sortable="custom"
          style="width: 20%">
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
import orderBy from 'lodash/orderBy'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data () {
    return {
      tableData: [{
        title: 'Deck Inspection',
        vessel_type: 'General Cargo Ship'
      }, {
        title: 'Underwater Inspection',
        vessel_type: 'General Cargo Ship'
      }]
    }
  },
  methods: {
    sortChange (event) {
      console.log(event)
      let order = event.order === 'descending' ? 'desc' : 'asc'
      this.tableData = orderBy(this.tableData, [event.prop], [order])
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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
</style>

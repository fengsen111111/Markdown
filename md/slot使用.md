### Ant Design of Vue上使用插槽
        <!-- 状态 -->
        <span slot="status" slot-scope="status">
          <a-tag v-if="status === 0" color="red">不显示</a-tag>
          <a-tag v-else-if="status === 1" color="green">显示</a-tag>
        </span>
### Element ui上使用slot
        <el-table-column prop="create_time" label="发生时间">
          <template slot-scope="scope">
            <span>{{ scope.row.create_time | formatDate }}</span>
          </template>
        </el-table-column>
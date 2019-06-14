<template>
  <div id="my-table">
    <el-data-table
      v-bind="tableConfig"
      paginationLayout="	total, sizes, prev, pager, next, jumper"
      :paginationSize="10"
      :paginationSizes="[10, 20, 30]"
    >
    </el-data-table>
  </div>
</template>

<script>
export default {
  data() {
    let searchForm = [
      {
        $type: 'input',
        $id: 'name',
        label: '组件名称',
        $el: {
          placeholder: '请输入'
        }
      },
      {
        $id: 'type',
        $type: 'select',
        label: '分类',
        $el: {
          placeholder: '请选择分类'
        },
        $options: [
          {
            label: '前端组件',
            value: '前端组件'
          },
          {
            label: '测试子组件',
            value: '测试子组件'
          },
          {
            label: '分布式工具',
            value: '分布式工具'
          },
          {
            label: '应用服务',
            value: '应用服务'
          },
          {
            label: '数据存储',
            value: '数据存储'
          }
        ]
      },
      {
        $id: 'status',
        $type: 'select',
        label: '状态',
        $el: {
          placeholder: '请选择状态'
        },
        $options: [
          {
            label: '上架',
            value: 1
          },
          {
            label: '下架',
            value: 0
          }
        ]
      }
    ]
    return {
      tableConfig: {
        // url: '/test',
        url: 'http://localhost:8000/mock/11/list',
        persistSelection: true,
        totalPath: 'total',
        extraButtons: [
          {
            text: '下架',
            atClick: row => Promise.resolve(),
            show: row => true
          }
        ],
        columns: [
          {type: 'selection'},
          {
            prop: 'name',
            label: '组件名称'
          },
          {
            prop: 'type',
            label: '分类'
          },
          {
            prop: 'version',
            label: '版本'
          },
          {
            prop: 'language',
            label: '开发语言'
          },
          {
            prop: 'date',
            label: '最后更新时间'
          },
          {
            prop: 'status',
            label: '状态'
          }
        ],
        searchForm,
        form: [
          {
            $type: 'input',
            $id: 'date',
            label: '最后更新时间',
            $el: {
              placeholder: '请输入'
            }
          },
          {
            $type: 'input',
            $id: 'language',
            label: '开发语言',
            $el: {
              placeholder: '请输入'
            }
          },
          ...searchForm
        ],
        // hasDelete: true,
        hasNew: true,
        hasView: true
      }
    }
  },
  methods: {}
}
</script>

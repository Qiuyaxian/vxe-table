<template>
  <div>
    <h1>{{ $t('app.aside.nav.commands') }}</h1>
    <p class="tip">将工具栏按钮或数据代理中常用的指令注册成全局可复用</p>
    <vxe-table
      resizable
      highlight-current-row
      highlight-hover-row
      highlight-current-column
      :data="tableData">
      <vxe-table-column field="name" title="app.api.title.prop" min-width="280" tree-node></vxe-table-column>
      <vxe-table-column field="desc" title="app.api.title.desc" min-width="200"></vxe-table-column>
      <vxe-table-column field="type" title="app.api.title.type" min-width="140"></vxe-table-column>
      <vxe-table-column field="enum" title="app.api.title.enum" min-width="150"></vxe-table-column>
      <vxe-table-column field="defVal" title="app.api.title.defVal" min-width="160"></vxe-table-column>
    </vxe-table>
    <h2>示例</h2>
    <pre>
      <pre-code class="typescript">{{ demoCodes[0] }}</pre-code>
      <pre-code class="html">{{ demoCodes[1] }}</pre-code>
      <pre-code class="typescript">{{ demoCodes[2] }}</pre-code>
    </pre>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue'

export default defineComponent({
  setup () {
    const tableData = ref([
      {
        name: 'add(code, callback)',
        desc: '添加一个',
        version: '',
        type: '',
        enum: '',
        defVal: 'code: string, callback: (params) => any',
        list: []
      },
      {
        name: 'mixin(options)',
        desc: '添加多个',
        version: '',
        type: '',
        enum: '',
        defVal: 'options: { [code: string]: (params) => any }',
        list: []
      },
      {
        name: 'delete(code)',
        desc: '删除',
        version: '',
        type: '',
        enum: '',
        defVal: 'code: string',
        list: []
      }
    ])
    return {
      tableData,
      demoCodes: [
        `
        import VXETable from 'vxe-table'

        VXETable.commands.add('exportBtn', (params) => {
          const { $table, code, button } = params
          $table.exportData()
        })
        `,
        `
        <vxe-toolbar :buttons="toolbarButtons"></vxe-toolbar>

        <vxe-table
          border
          :data="tableData">
          <vxe-table-column type="seq" width="60"></vxe-table-column>
          <vxe-table-column field="name" title="Name" :edit-render="{name: 'input'}"></vxe-table-column>
          <vxe-table-column field="sex" title="sex"></vxe-table-column>
          <vxe-table-column field="age" title="Age"></vxe-table-column>
        </vxe-table>
        `,
        `
        import { defineComponent, ref } from 'vue'

        export default defineComponent({
          setup () {
            const toolbarButtons = ref([
              { code: 'exportBtn', name: '导出.csv' }
            ])
            const tableData = ref([
              { id: 10001, name: 'Test1', role: 'Develop', sex: 'Man', age: 28, address: 'Shenzhen' },
              { id: 10002, name: 'Test2', role: 'Test', sex: 'Women', age: 22, address: 'Guangzhou' },
              { id: 10003, name: 'Test3', role: 'PM', sex: 'Man', age: 32, address: 'Shanghai' },
              { id: 10004, name: 'Test4', role: 'Designer', sex: 'Women ', age: 24, address: 'Shanghai' }
            ])
            return {
              toolbarButtons,
              tableData
            }
          }
        })
        `
      ]
    }
  }
})
</script>

<template>
  <div>
    <h1>{{ $t('app.aside.nav.formats') }}</h1>
    <p class="tip">将列的格式化函数注册成全局可复用，通过 <table-column-api-link prop="formatter"/> 调用</p>
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
        name: 'add(name, callback)',
        desc: '添加一个',
        version: '',
        type: '',
        enum: '',
        defVal: 'name: string, callback: (params) => string | number',
        list: []
      },
      {
        name: 'mixin(options)',
        desc: '添加多个',
        version: '',
        type: '',
        enum: '',
        defVal: 'options: { [name: string]: (params) => string | number }',
        list: []
      },
      {
        name: 'delete(name)',
        desc: '删除',
        version: '',
        type: '',
        enum: '',
        defVal: 'name',
        list: []
      }
    ])
    return {
      tableData,
      demoCodes: [
        `
        import VXETable from 'vxe-table'
        import XEUtils from 'xe-utils'

        // 格式金额，默认2位数
        VXETable.formats.add('myAmount', ({ cellValue }, digits = 2) => {
          return XEUtils.commafy(XEUtils.toNumber(cellValue), { digits })
        })
        `,
        `
        <vxe-table
          border
          :data="tableData">
          <vxe-table-column type="seq" width="60"></vxe-table-column>
          <vxe-table-column field="name" title="Name"></vxe-table-column>
          <vxe-table-column field="num1" title="默认两位小数" formatter="myAmount"></vxe-table-column>
          <vxe-table-column field="num2" title="保留3位小数" :formatter="['myAmount', 3]"></vxe-table-column>
        </vxe-table>
        `,
        `
        import { defineComponent, ref } from 'vue'

        export default defineComponent({
          setup () {
            const tableData = ref([
              { id: 10001, name: 'Test1', role: 'Develop', num2: 22, num1: 28, address: 'Shenzhen' },
              { id: 10002, name: 'Test2', role: 'Test', num2: 10, num1: 22, address: 'Guangzhou' },
              { id: 10003, name: 'Test3', role: 'PM', num2: 5, num1: 32, address: 'Shanghai' },
              { id: 10004, name: 'Test4', role: 'Designer', num2: 20, num1: 24, address: 'Shanghai' }
            ]
            return {
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

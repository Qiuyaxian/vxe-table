<template>
  <div>
    <p class="tip">改变图标，通过设置 <table-api-link prop="filter-config"/>={<table-api-link prop="iconMatch"/>, <table-api-link prop="iconMatch"/>} 局部替换默认的图标，例如第三方图标库：font-awesome、inconfont</p>

    <vxe-table
      border
      highlight-hover-row
      height="400"
      :filter-config="{iconNone: 'fa fa-wheelchair', iconMatch: 'fa fa-wheelchair-alt'}"
      :loading="demo1.loading"
      :data="demo1.tableData">
      <vxe-table-column type="seq" width="60"></vxe-table-column>
      <vxe-table-column field="name" title="Name"></vxe-table-column>
      <vxe-table-column field="role" title="Role" :filters="[{label: '前端', value: '前端'}, {label: '后端', value: '后端'}]"></vxe-table-column>
      <vxe-table-column field="sex" title="Sex" sortable :filter-multiple="false" :filters="[{label: 'Man', value: '1'}, {label: 'Woman', value: '0'}]"></vxe-table-column>
      <vxe-table-column field="age" title="Age"></vxe-table-column>
      <vxe-table-column field="address" title="Address" sortable></vxe-table-column>
    </vxe-table>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <pre-code class="xml">{{ demoCodes[0] }}</pre-code>
      <pre-code class="typescript">{{ demoCodes[1] }}</pre-code>
    </pre>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'

export default defineComponent({
  setup () {
    const demo1 = reactive({
      loading: false,
      tableData: [] as any[]
    })

    const findList = (): Promise<void> => {
      demo1.loading = true
      return new Promise(resolve => {
        setTimeout(() => {
          demo1.tableData = [
            { id: 10001, name: 'Test1', role: 'Develop', sex: '0', age: 28, amount: 888, address: 'vxe-table 从入门到放弃' },
            { id: 10002, name: 'Test2', role: 'Test', sex: '1', age: 22, amount: 666, address: 'Guangzhou' },
            { id: 10003, name: 'Test3', role: 'PM', sex: '1', age: 32, amount: 89, address: 'Shanghai' },
            { id: 10004, name: 'Test4', role: 'Designer', sex: '0', age: 23, amount: 1000, address: 'vxe-table 从入门到放弃' },
            { id: 10005, name: 'Test5', role: 'Develop', sex: '0', age: 30, amount: 999, address: 'Shanghai' },
            { id: 10006, name: 'Test6', role: 'Designer', sex: '0', age: 21, amount: 998, address: 'vxe-table 从入门到放弃' },
            { id: 10007, name: 'Test7', role: 'Test', sex: '1', age: 29, amount: 2000, address: 'vxe-table 从入门到放弃' },
            { id: 10008, name: 'Test8', role: 'Develop', sex: '1 ', age: 35, amount: 999, address: 'vxe-table 从入门到放弃' }
          ]
          demo1.loading = false
          resolve()
        }, 300)
      })
    }

    findList()

    return {
      demo1,
      demoCodes: [
        `
        <vxe-table
          border
          highlight-hover-row
          height="400"
          :filter-config="{iconNone: 'fa fa-wheelchair', iconMatch: 'fa fa-wheelchair-alt'}"
          :loading="demo1.loading"
          :data="demo1.tableData">
          <vxe-table-column type="seq" width="60"></vxe-table-column>
          <vxe-table-column field="name" title="Name"></vxe-table-column>
          <vxe-table-column field="role" title="Role" :filters="[{label: '前端', value: '前端'}, {label: '后端', value: '后端'}]"></vxe-table-column>
          <vxe-table-column field="sex" title="Sex" sortable :filter-multiple="false" :filters="[{label: 'Man', value: '1'}, {label: 'Woman', value: '0'}]"></vxe-table-column>
          <vxe-table-column field="age" title="Age"></vxe-table-column>
          <vxe-table-column field="address" title="Address" sortable></vxe-table-column>
        </vxe-table>
        `,
        `
        import { defineComponent, reactive } from 'vue'

        export default defineComponent({
          setup () {
            const demo1 = reactive({
              loading: false,
              tableData: [] as any[]
            })

            const findList = (): Promise<void> => {
              demo1.loading = true
              return new Promise(resolve => {
                setTimeout(() => {
                  demo1.tableData = [
                    { id: 10001, name: 'Test1', role: 'Develop', sex: '0', age: 28, amount: 888, address: 'vxe-table 从入门到放弃' },
                    { id: 10002, name: 'Test2', role: 'Test', sex: '1', age: 22, amount: 666, address: 'Guangzhou' },
                    { id: 10003, name: 'Test3', role: 'PM', sex: '1', age: 32, amount: 89, address: 'Shanghai' },
                    { id: 10004, name: 'Test4', role: 'Designer', sex: '0', age: 23, amount: 1000, address: 'vxe-table 从入门到放弃' },
                    { id: 10005, name: 'Test5', role: 'Develop', sex: '0', age: 30, amount: 999, address: 'Shanghai' },
                    { id: 10006, name: 'Test6', role: 'Designer', sex: '0', age: 21, amount: 998, address: 'vxe-table 从入门到放弃' },
                    { id: 10007, name: 'Test7', role: 'Test', sex: '1', age: 29, amount: 2000, address: 'vxe-table 从入门到放弃' },
                    { id: 10008, name: 'Test8', role: 'Develop', sex: '1 ', age: 35, amount: 999, address: 'vxe-table 从入门到放弃' }
                  ]
                  demo1.loading = false
                  resolve()
                }, 300)
              })
            }

            findList()

            return {
              demo1
            }
          }
        })
        `
      ]
    }
  }
})
</script>

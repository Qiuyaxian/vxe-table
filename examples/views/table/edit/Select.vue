<template>
  <div>
    <p class="tip">单元格点击编辑，还可以通过 <table-column-api-link prop="autoselect"/> 开启默认选中</p>

    <vxe-table
      border
      resizable
      show-overflow
      :data="demo1.tableData"
      :edit-config="{trigger: 'click', mode: 'cell'}">
      <vxe-table-column type="seq" width="60"></vxe-table-column>
      <vxe-table-colgroup title="分组1">
        <vxe-table-column field="name" title="Name" :edit-render="{name: 'input', autoselect: true}"></vxe-table-column>
        <vxe-table-column field="nickname" title="Nickname" :edit-render="{name: 'input', autoselect: true}"></vxe-table-column>
        <vxe-table-column field="sex" title="Sex" :edit-render="{name: '$select', optionGroups: demo1.sexGriupList}"></vxe-table-column>
      </vxe-table-colgroup>
      <vxe-table-colgroup title="分组1">
        <vxe-table-column field="date12" title="Date" :edit-render="{name: '$input', props: {type: 'date'}, autoselect: true}"></vxe-table-column>
      </vxe-table-colgroup>
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
      tableData: [
        { id: 10001, name: 'Test1', nickname: 'T1', role: 'Develop', sex: '0', sex2: ['0'], num1: 40, age: 28, address: 'Shenzhen', date12: '', date13: '' },
        { id: 10002, name: 'Test2', nickname: 'T2', role: 'Designer', sex: '1', sex2: ['0', '1'], num1: 20, age: 22, address: 'Guangzhou', date12: '', date13: '2020-08-20' },
        { id: 10003, name: 'Test3', nickname: 'T3', role: 'Test', sex: '0', sex2: ['1'], num1: 200, age: 32, address: 'Shanghai', date12: '2020-09-10', date13: '' },
        { id: 10004, name: 'Test4', nickname: 'T4', role: 'Designer', sex: '1', sex2: ['1'], num1: 30, age: 23, address: 'Shenzhen', date12: '', date13: '2020-12-04' }
      ],
      sexGriupList: [
        {
          label: '第一分组',
          options: [
            { value: '0', label: '女' }
          ]
        },
        {
          label: '第二分组',
          options: [
            { value: '1', label: '男' }
          ]
        },
        {
          label: '其他',
          options: [
            { value: '2', label: '无' }
          ]
        }
      ]
    })
    return {
      demo1,
      demoCodes: [
        `
        <vxe-table
          border
          resizable
          show-overflow
          :data="demo1.tableData"
          :edit-config="{trigger: 'click', mode: 'cell'}">
          <vxe-table-column type="seq" width="60"></vxe-table-column>
          <vxe-table-colgroup title="分组1">
            <vxe-table-column field="name" title="Name" :edit-render="{name: 'input', autoselect: true}"></vxe-table-column>
            <vxe-table-column field="nickname" title="Nickname" :edit-render="{name: 'input', autoselect: true}"></vxe-table-column>
            <vxe-table-column field="sex" title="Sex" :edit-render="{name: '$select', optionGroups: demo1.sexGriupList}"></vxe-table-column>
          </vxe-table-colgroup>
          <vxe-table-colgroup title="分组1">
            <vxe-table-column field="date12" title="Date" :edit-render="{name: '$input', props: {type: 'date'}, autoselect: true}"></vxe-table-column>
          </vxe-table-colgroup>
        </vxe-table>
        `,
        `
        import { defineComponent, reactive } from 'vue'

        export default defineComponent({
          setup () {
            const demo1 = reactive({
              tableData: [],
              sexGriupList: [
                {
                  label: '第一分组',
                  options: [
                    { value: '0', label: '女' }
                  ]
                },
                {
                  label: '第二分组',
                  options: [
                    { value: '1', label: '男' }
                  ]
                },
                {
                  label: '其他',
                  options: [
                    { value: '2', label: '无' }
                  ]
                }
              ]
            })
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

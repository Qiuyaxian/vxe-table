<template>
  <div>
    <h2>{{ $t('app.aside.nav.checkbox') }}</h2>
    <p class="tip">复选框、复选组</p>

    <p>
      <vxe-checkbox v-model="demo1.value1" content="默认尺寸"></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value2" size="medium" content="中等尺寸"></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value3" size="small" content="小型尺寸"></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value4" size="mini" content="超小尺寸"></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value5" content="默认尺寸" indeterminate></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value6" size="medium" content="中等尺寸" indeterminate></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value7" size="small" content="小型尺寸" indeterminate></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value8" size="mini" content="超小尺寸" indeterminate></vxe-checkbox>
    </p>

    <p>
      <vxe-checkbox v-model="demo1.value9" content="复选1"></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value10" content="复选2" disabled></vxe-checkbox>
      <vxe-checkbox v-model="demo1.value11" content="复选3"></vxe-checkbox>
    </p>

    <p>
      <vxe-checkbox-group v-model="demo1.value12">
        <vxe-checkbox label="1" content="HTML"></vxe-checkbox>
        <vxe-checkbox label="2" content="CSS"></vxe-checkbox>
        <vxe-checkbox label="3" content="Javascript"></vxe-checkbox>
        <vxe-checkbox label="4" content="SASS"></vxe-checkbox>
        <vxe-checkbox label="5" content="LESS"></vxe-checkbox>
      </vxe-checkbox-group>
    </p>

    <pre>
      <pre-code>
        | Tab | 切换到上一个 |
        | Shift + Tab | 切换到下一个 |
        | Spacebar | 按下勾选 |
      </pre-code>
    </pre>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <pre-code class="html">{{ demoCodes[0] }}</pre-code>
      <pre-code class="typescript">{{ demoCodes[1] }}</pre-code>
    </pre>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue'

export default defineComponent({
  setup  () {
    const demo1 = reactive({
      value1: null,
      value2: null,
      value3: null,
      value4: null,
      value5: false,
      value6: false,
      value7: false,
      value8: false,
      value9: true,
      value10: true,
      value11: false,
      value12: ['3']
    })
    return {
      demo1,
      demoCodes: [
        `
        <p>
          <vxe-checkbox v-model="demo1.value1" content="默认尺寸"></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value2" size="medium" content="中等尺寸"></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value3" size="small" content="小型尺寸"></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value4" size="mini" content="超小尺寸"></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value5" content="默认尺寸" indeterminate></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value6" size="medium" content="中等尺寸" indeterminate></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value7" size="small" content="小型尺寸" indeterminate></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value8" size="mini" content="超小尺寸" indeterminate></vxe-checkbox>
        </p>

        <p>
          <vxe-checkbox v-model="demo1.value9" content="复选1"></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value10" content="复选2" disabled></vxe-checkbox>
          <vxe-checkbox v-model="demo1.value11" content="复选3"></vxe-checkbox>
        </p>

        <p>
          <vxe-checkbox-group v-model="demo1.value12">
            <vxe-checkbox label="1" content="HTML"></vxe-checkbox>
            <vxe-checkbox label="2" content="CSS"></vxe-checkbox>
            <vxe-checkbox label="3" content="Javascript"></vxe-checkbox>
            <vxe-checkbox label="4" content="SASS"></vxe-checkbox>
            <vxe-checkbox label="5" content="LESS"></vxe-checkbox>
          </vxe-checkbox-group>
        </p>
        `,
        `
        import { defineComponent } from 'vue'

        export default defineComponent({
          setup  () {
            const demo1 = reactive({
              value1: null,
              value2: null,
              value3: null,
              value4: null,
              value5: false,
              value6: false,
              value7: false,
              value8: false,
              value9: true,
              value10: true,
              value11: false,
              value12: ['3']
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

<template>
  <div class="nut-invoice">
    <nut-form ref="formRef" :model-value="formValue">
      <nut-form-item
        v-for="(item, index) of data"
        :key="index"
        :label="item.label"
        :required="item.required"
        :rules="item.rules"
        :prop="item.formItemProp"
      >
        <template v-if="item.type === 'radio'">
          <nut-radio-group v-model="formValue[item.formItemProp]">
            <nut-radio
              v-for="(radioItem, radioIndex) of item.radioLabel"
              :key="radioIndex"
              shape="button"
              :label="radioItem.label"
            >
              {{ radioItem.label }}
            </nut-radio>
          </nut-radio-group>
        </template>
        <template v-else>
          <nut-input
            v-model="formValue[item.formItemProp]"
            class="nut-input-text"
            :placeholder="item.placeholder"
            type="text"
          />
        </template>
      </nut-form-item>
    </nut-form>
    <div v-if="submit" class="nut-invoice__submit">
      <nut-button type="primary" block @click="submitFun">提交审批</nut-button>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
import NutForm from '../form'
import NutFormItem from '../formitem'
import NutRadio from '../radio'
import NutRadioGroup from '../radiogroup'
import NutButton from '../button'
import NutInput from '../input/index.vue'
import type { InvoiceDataItem } from './types'

defineOptions({
  name: 'NutInvoice'
})

export type InvoiceProps = Partial<{
  data: InvoiceDataItem[]
  formValue: any
  submit: boolean
}>

withDefaults(defineProps<InvoiceProps>(), {
  data: () => [],
  formValue: () => {},
  submit: true
})

const emit = defineEmits(['submit', 'scrollBottom'])

const formRef = ref()

const submitFun = () => {
  formRef.value.validate().then(({ valid, errors }: any) => {
    emit('submit', valid, errors)
  })
}
</script>

<template>
  <nut-cell @click="visible = true"> 请选择配送时间 </nut-cell>
  <nut-time-select
    v-model:visible="visible"
    style="height: 50%"
    :current-key="key"
    :current-time="time"
    @select="handleSelect"
  >
    <template #title> 标题 </template>
    <template #pannel>
      <nut-time-pannel name="2月23日(今天)" pannel-key="0" @change="onChange"></nut-time-pannel>
      <nut-time-pannel name="2月24日(星期三)" pannel-key="1" @change="onChange"></nut-time-pannel>
    </template>
    <template #detail>
      <nut-time-detail :times="times" @select="onSelect"></nut-time-detail>
    </template>
  </nut-time-select>
</template>
<script setup>
import { ref, onMounted } from 'vue'
const visible = ref(false)
const key = ref(0)
const time = ref([])
const times = ref([
  {
    key: 0,
    list: ['9:00-10:00', '10:00-11:00', '11:00-12:00']
  },
  {
    key: 1,
    list: ['9:00-10:00', '10:00-11:00']
  }
])

const onChange = (pannelKey) => {
  key.value = pannelKey
  time.value = []
  time.value.push({
    key: pannelKey,
    list: []
  })
}

const onSelect = (item) => {
  let curTimeIndex = time.value[0]['list'].findIndex(time => time === item)
  if (curTimeIndex === -1) {
    time.value[0]['list'].push(item)
  } else {
    time.value[0]['list'].splice(curTimeIndex, 1)
  }
}

const handleSelect = (obj) => {
  console.log(obj)
}

onMounted(() => {
  time.value.push({
    key: key.value,
    list: []
  })
})
</script>

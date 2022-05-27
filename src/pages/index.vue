<script lang="ts" setup>
import * as html2img from 'html-to-image'
import saveAs from 'file-saver'

const data = reactive({
  sentence: '我本可以忍受黑暗，如果我不曾见过太阳',
  author: '艾米莉·狄金森',
  bgColor: '#007cb6',
})

const ele = ref<HTMLElement>()

async function snapshot() {
  if (!ele.value) return

  const blob = await html2img.toBlob(ele.value, {
    style: {
      boxShadow: '0 0 30px rgba(177, 177, 177, 0.747)',
    },
  })

  if (blob) {
    saveAs(blob, 'shared-card.png')
  }
}
</script>

<template>
  <div class="gap-y-2" flex="~ col" w="screen-md" m="auto" h="screen">
    <h1>卡片分享</h1>

    <k-row class="items-center">
      <span> 句子： </span>
      <k-input v-model="data.sentence" flex="1" block></k-input>
    </k-row>
    <k-row class="items-center">
      <span> 作者： </span>
      <k-input v-model="data.author" flex="1" block></k-input>
    </k-row>

    <k-row class="items-center">
      <span> 背景颜色： </span>
      <input v-model="data.bgColor" type="color" />
      <k-button @click="snapshot">保存到本地</k-button>
    </k-row>

    <div bg="gray-100" p="8" m="t-4">
      <div w="fit" m="auto">
        <div ref="ele">
          <card-style-one v-bind="data"></card-style-one>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="less"></style>

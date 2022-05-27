<script lang="ts" setup>
import dayjs from 'dayjs'

defineProps<{
  sentence: string
  author: string
  bgColor: string
}>()
</script>

<template>
  <div class="card-style-one">
    <div class="content">
      <div class="datetime">
        {{ dayjs().format('YYYY-MM-DD') }}
      </div>
      <div flex="~ 1" class="items-center justify-center">
        <div class="sentence">
          {{ sentence }}
        </div>
      </div>

      <div class="items-end" flex="~ col" justify="end">
        <div>—— {{ author }}</div>
        <div m="t-4"></div>
      </div>
    </div>
    <!--  -->
  </div>
</template>

<style lang="less" scoped>
//
.card-style-one {
  @size: 350px;
  @radius: 20px;

  width: @size;
  height: @size;
  border-radius: @radius;
  background: white;
  padding: 15px;

  .content {
    border-radius: @radius;
    padding: 20px;
    color: white;
    background-color: v-bind('bgColor');

    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }

  .sentence {
    font-size: x-large;
    position: relative;
    padding: 20px;
    line-height: 1.5em;
    word-break: break-all;

    &::before,
    &::after {
      position: relative;
      font-size: 1.5em;
      color: rgba(230, 230, 230, 0.389);
    }

    &::before {
      content: '“';
      top: -0px;
      left: -10px;
    }

    &::after {
      content: '”';
      bottom: -0px;
      right: -10px;
    }
  }
}
</style>

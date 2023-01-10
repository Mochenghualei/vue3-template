<template>
  <div class="container">
    <div>
      <el-button plain type="success" @click="open2">success</el-button>
      <el-button plain type="warning" @click="open3">warning</el-button>
      <el-button plain type="info" @click="open1">message</el-button>
      <el-button plain type="danger" @click="open4">error</el-button>
    </div>
    <div>
      <el-button plain type="primary" @click="countStore.increment()">count : {{ countStore.count }}</el-button>
    </div>
    <div>
      <el-button @click="toggleDark()">
        <el-icon>
          <component :is="icon"></component>
        </el-icon>
        <span>{{ isDark ? 'Dark' : 'Light' }}</span>
      </el-button>
    </div>
  </div>
</template>

<script setup lang="ts">
import { useCountStore } from '@/store/modules/count'

const countStore = useCountStore()

const isDark = useDark({})

const toggleDark = useToggle(isDark)

const icon = computed(() => (isDark.value ? 'moon' : 'sunny'))

onMounted(() => {
  sayHello()
})

const open1 = () => {
  ElMessage('this is a message.')
}
const open2 = () => {
  ElMessage({
    message: 'Congrats, this is a success message.',
    type: 'success',
  })
}
const open3 = () => {
  ElMessage({
    message: 'Warning, this is a warning message.',
    type: 'warning',
  })
}
const open4 = () => {
  ElMessage.error('Oops, this is a error message.')
}
</script>

<style scoped lang="scss">
.container {
  height: 100vh;
  width: 100vw;
  display: flex;
  flex-flow: column wrap;
  justify-content: center;
  align-items: center;
  gap: 10px;
  h1 {
    font-size: 2rem;
  }
}
</style>

<script setup lang="ts">
import { computed } from 'vue'
import { NTabPane, NTabs } from 'naive-ui'
import Style from './tabs/Style.vue'
import About from './tabs/About.vue'
import Users from './tabs/Users.vue'
import UserInfo from './tabs/UserInfo.vue'
import { RoundCardModal } from '@/components/common'

const props = defineProps<{
  visible: boolean
}>()

const emit = defineEmits<{
  (e: 'update:visible', visible: boolean): void
}>()

const show = computed({
  get: () => props.visible,
  set: (visible: boolean) => {
    emit('update:visible', visible)
  },
})
</script>

<template>
  <div>
    <RoundCardModal v-model:show="show" title="设置" style="max-height: 700px;">
      <NTabs type="line" animated>
        <NTabPane name="style" tab="样式">
          <Style />
        </NTabPane>
        <NTabPane name="userInfo" tab="登录信息">
          <UserInfo />
        </NTabPane>
        <NTabPane name="about" tab="关于">
          <About />
        </NTabPane>
        <NTabPane name="password" tab="账号管理">
          <Users />
        </NTabPane>
      </NTabs>
    </RoundCardModal>
  </div>
</template>

<style scoped>
.text-shadow{
  text-shadow: 0px 0px 5px gray;
}
</style>

<template>
  <div
    class="bg-gray-50 text-slate-700 dark:text-slate-500 dark:bg-slate-800 w-screen h-screen"
  >
    <gva-header />
    <div class="flex flex-row w-full gva-container pt-16 box-border h-full">
      <gva-aside
        v-if="
          config.side_mode === 'normal' || config.side_mode === 'sidebar' ||
          (device === 'mobile' && config.side_mode == 'head') ||
          (device === 'mobile' && config.side_mode == 'combination')
        "
      />
      <gva-aside
        v-if="config.side_mode === 'combination' && device !== 'mobile'"
        mode="normal"
      />
      <div class="flex-1 px-2 w-0 h-full">
        <gva-tabs v-if="config.showTabs" />
        <div
          class="overflow-auto"
          :class="config.showTabs ? 'gva-container2' : 'gva-container pt-1'"
        >
          <router-view v-if="reloadFlag" v-slot="{ Component, route }">
            <div
              id="gva-base-load-dom"
              class="gva-body-h bg-gray-50 dark:bg-slate-800"
            >
              <transition mode="out-in" :name="route.meta.transitionType || config.transition_type">
                <keep-alive :include="routerStore.keepAliveRouters">
                  <component :is="Component" :key="route.fullPath" />
                </keep-alive>
              </transition>
            </div>
          </router-view>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
  import GvaAside from '@/view/layout/aside/index.vue'
  import GvaHeader from '@/view/layout/header/index.vue'
  import useResponsive from '@/hooks/responsive'
  import GvaTabs from './tabs/index.vue'
  import { emitter } from '@/utils/bus.js'
  import { ref, onMounted, nextTick, reactive, watchEffect } from 'vue'
  import { useRouter, useRoute } from 'vue-router'
  import { useRouterStore } from '@/pinia/modules/router'
  import { useUserStore } from '@/pinia/modules/user'
  import { useAppStore } from '@/pinia'
  import { storeToRefs } from 'pinia'
  import '@/style/transition.scss'
  const appStore = useAppStore()
  const { config, isDark, device } = storeToRefs(appStore)

  defineOptions({
    name: 'GvaLayout'
  })

  useResponsive(true)
  const font = reactive({
    color: 'rgba(0, 0, 0, .15)'
  })

  watchEffect(() => {
    font.color = isDark.value ? 'rgba(255,255,255, .15)' : 'rgba(0, 0, 0, .15)'
  })

  const router = useRouter()
  const route = useRoute()
  const routerStore = useRouterStore()

  onMounted(() => {
    // 挂载一些通用的事件
    emitter.on('reload', reload)
    if (userStore.loadingInstance) {
      userStore.loadingInstance.close()
    }
  })

  const userStore = useUserStore()

  const reloadFlag = ref(true)
  let reloadTimer = null
  const reload = async () => {
    if (reloadTimer) {
      window.clearTimeout(reloadTimer)
    }
    reloadTimer = window.setTimeout(async () => {
      if (route.meta.keepAlive) {
        reloadFlag.value = false
        await nextTick()
        reloadFlag.value = true
      } else {
        const title = route.meta.title
        router.push({ name: 'Reload', params: { title } })
      }
    }, 400)
  }
</script>

<style lang="scss"></style>

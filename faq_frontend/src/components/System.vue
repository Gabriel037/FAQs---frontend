<template>
  <div class="system-content">
    <SystemIndex />
    <SystemFaqs />
  </div>
</template>

<script>
import SystemIndex from '@/components/SystemIndex'
import SystemFaqs from '@/components/SystemFaqs'

export default {
  name: 'System',
  components: { SystemIndex, SystemFaqs },
}
</script>

<style scoped>
  .system-content {
    background-color: var(--azul);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
</style>

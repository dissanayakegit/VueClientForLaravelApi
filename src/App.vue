<template>
  <div id="app">
    <TheNavigation />
    <router-view/>
  </div>
</template>

<script>
// @ is an alias to /src
import TheNavigation from '@/components/TheNavigation'

export default {
  name: 'Home',
  components: {
    TheNavigation
  }
}
</script>

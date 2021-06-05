<template>
  <div>
      <Navbar @update-selected-tab='updateSelectedTab'></Navbar>
      <Characters v-if="tab==1"></Characters>
  </div>
</template>

<script>
import Characters from '../components/Characters'
import Navbar from '../components/Navbar'

export default {
    components: {
        Characters,
        Navbar
    },
    data() {
        return {
            tab: 0
        }
    },
    methods: {
        updateSelectedTab(_tab) {
            this.tab = _tab;
        }
    }
}

</script>

<style scoped>
</style>
<template>
    <div>
        <Navbar @update-selected-tab='updateSelectedTab'></Navbar>
        <Daily v-if="tab==0"></Daily>
        <Characters v-if="tab==1"></Characters>
        <Weapons v-if="tab==2"></Weapons>
    </div>
</template>

<script>
import Characters from '../components/Characters'
import Navbar from '../components/Navbar'
import Daily from '../components/Daily'
import Weapons from '../components/Weapons'

export default {
    components: {
        Characters,
        Navbar,
        Daily,
        Weapons
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
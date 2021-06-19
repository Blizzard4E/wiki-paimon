<template>
    <main>
        <WeaponDisplay v-bind:selectedWeapon="selectedWeapon"></WeaponDisplay>
        <section class="background">
            <WeaponSelection @update-selected-weap="updateSelectedWeapon"></WeaponSelection>
        </section>
    </main>
</template>

<script>
import WeaponDisplay from './Weapons/WeaponDisplay'
import WeaponSelection from './Weapons/WeaponSelection'

export default {
    components: {
        WeaponDisplay,
        WeaponSelection
    },
    data() {
        return {
            selectedWeapon: ''
        }
    },
    methods: {
        updateSelectedWeapon(weapon) {
            this.selectedWeapon = weapon;
        }
    }
}
</script>

<style scoped>
    .background {
        background: #ece6da;
    }
</style>
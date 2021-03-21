<template>
    <main>
        <section class="background">
            <CharacterSelection @update-selected-char='updateSelectedChar'></CharacterSelection>
        </section>
        <section>
            <AttackAbilities v-bind:selectedChar="character"></AttackAbilities>
            <PassiveAbilities v-bind:selectedChar="character"></PassiveAbilities>
        </section>
    </main>
</template>

<script>
import CharacterSelection from './Characters/CharacterSelection';
import AttackAbilities from './Characters/AttackAbilities';
import PassiveAbilities from './Characters/PassiveAbilities';

export default {
    components: {
        CharacterSelection,
        AttackAbilities,
        PassiveAbilities
    },
    data() {
        return {
            character: {}
        }
    },
    methods: {
        updateSelectedChar(_character) {
            this.character = _character;
            console.log(this.character);
        }
    }
}
</script>

<style scoped>
    .background {
        background: #101520;
    }
</style>
<template>
    <main>
        <section class="background">
            <CharacterSelection @update-selected-char='updateSelectedChar'></CharacterSelection>
        </section>
        <section>
            <AttackAbilities></AttackAbilities>
        </section>
    </main>
</template>

<script>
import CharacterSelection from './Characters/CharacterSelection';
import AttackAbilities from './Characters/AttackAbilities';

export default {
    components: {
        CharacterSelection,
        AttackAbilities
    },
    data() {
        return {
            selectedChar: ''
        }
    },
    methods: {
        updateSelectedChar(charName) {
            this.selectedChar = charName;
            console.log(this.selectedChar);
        }
    }
}
</script>

<style scoped>
    .background {
        background: #101520;
    }
</style>
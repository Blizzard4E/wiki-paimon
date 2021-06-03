<template>
    <main>
        <section class="background">
            <CharacterSelection v-bind:selectedChar="character" @update-selected-char='updateSelectedChar'></CharacterSelection>
        </section>
        <section>
            <div v-show="character.name=='Aether' || character.name=='Lumine'">
                <ElementSelection v-bind:selectedChar="character" @update-selected-char='updateSelectedChar'></ElementSelection>
            </div>
            <AttackAbilities v-bind:selectedChar="character"></AttackAbilities>
            <PassiveAbilities v-bind:selectedChar="character"></PassiveAbilities>
        </section>
    </main>
</template>

<script>
import CharacterSelection from './Characters/CharacterSelection';
import AttackAbilities from './Characters/AttackAbilities';
import PassiveAbilities from './Characters/PassiveAbilities';
import ElementSelection from './Characters/ElementSelection';

export default {
    components: {
        CharacterSelection,
        AttackAbilities,
        PassiveAbilities,
        ElementSelection
    },
    data() {
        return {
            character: {}
        }
    },
    methods: {
        updateSelectedChar(_character) {
            this.character = _character;
            console.log(this.character.name);
        }
    }
}
</script>

<style scoped>
    .background {
        background: #101520;
    }
</style>
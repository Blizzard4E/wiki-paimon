<template>
    <section class="background">
        <CharacterSelection @update-selected-char='updateSelectedChar'></CharacterSelection>
    </section>
</template>

<script>
import CharacterSelection from './CharacterSelection/CharacterSelection'

export default {
    components: {
        CharacterSelection
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
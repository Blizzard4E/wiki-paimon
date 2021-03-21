<template>
    <article class="character-selection container">
        <section class="character-selector">
            <h1 v-if="triggerAnimation" v-bind:class="{
                characterSelected: true,
                pyro: selectedChar.element == 'Pyro',
                anemo: selectedChar.element == 'Anemo',
                geo: selectedChar.element == 'Geo',
                hydro: selectedChar.element == 'Hydro',
                cryo: selectedChar.element == 'Cryo',
                electro: selectedChar.element == 'Electro',
                dendro: selectedChar.element == 'Dendro'
                                }">{{selectedChar.name}}</h1>
            <div v-else style="min-height: 153px"></div>
            <ul class="character-list">
                <li v-for="character in characters" :key="character.id">
                    <a @click="updateSelectedChar(character)">{{character}}</a>
                </li>
            </ul>
        </section>
        <figure class="character-image">
            <img v-if="triggerAnimation" :src="selectedChar.cutout" alt="Character Art">
        </figure>
        <summary class="character-summary">
            <div v-if="triggerAnimation">
                <h2 class="character-title">{{selectedChar.title}}</h2>
                <p class="character-intro">{{selectedChar.intro}}</p>
                <img class="character-element" :src="elementIcon" alt="Character Element Image">
            </div>
        </summary>
    </article>
</template>

<script>
import characters from '../../data/characters.json';
import elementIcons from '../../data/elements_icon';

export default {
    data() {
        return {
            characters: [],
            selectedChar: {},
            elementIcon: null,
            triggerAnimation: false
        }
    },
    methods: {
        async updateSelectedChar(charName) {

            //Stop Rendering Image
            this.triggerAnimation = false;

            //Import Selected Character From Data
            let newSelectedChar = await import(`../../data/characters/${charName.replace(' ', '')}.json`);
            this.selectedChar = newSelectedChar;

            //Update Selected Character For Parents
            this.$emit('update-selected-char', this.selectedChar);

            //Change Element Icons
            if(this.selectedChar.element == "Anemo")
            {
                this.elementIcon = elementIcons.Anemo;
            }
            else if(this.selectedChar.element == "Hydro")
            {
                this.elementIcon = elementIcons.Hydro;
            }
            else if(this.selectedChar.element == "Pyro")
            {
                this.elementIcon = elementIcons.Pyro;
            }
            else if(this.selectedChar.element == "Geo")
            {
                this.elementIcon = elementIcons.Geo;
            }
            else if(this.selectedChar.element == "Dendro")
            {
                this.elementIcon = elementIcons.Dendro;
            }
            else if(this.selectedChar.element == "Electro")
            {
                this.elementIcon = elementIcons.Electro;
            }
            else if(this.selectedChar.element == "Cryo")
            {
                this.elementIcon = elementIcons.Cryo;
            }
            
            //Remove Selected Character from Character List
            let newCharList = characters;
            newCharList = newCharList.filter(character => character !== this.selectedChar.name.toLowerCase());
            this.characters = newCharList;

            //Start rendering image to start animation again
            this.triggerAnimation = true;
        }
    },
    mounted() {
        this.characters = characters;
        this.updateSelectedChar('xiao');
    }
}
</script>

<style scoped>
    .character-selection {
        display: grid;
        grid-template-columns: 3fr 4fr 2fr;
    }
    .character-image {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .character-image > img {
        height: 39.5rem;
        transition: 0.2s;
        animation: scale-up 0.5s linear, moving 4s infinite linear;
    }
    @keyframes scale-up {
        from {transform: scale(0.5);}
        to {transform: scale(1);}
    }
    @keyframes moving {
        0% {transform: translateY(8px);}
        50% {transform: translateY(-8px);}
        100% {transform: translateY(8px);}
    }
    .character-selector {
        max-width: 400px;
        overflow-x: visible;
        overflow-y: visible;
    }
    .character-list {
        min-height: 30rem;
        max-height: 30rem;
        overflow-y: scroll;
        overflow-x: visible;
        scroll-snap-align: center;
        transition: 0.3s;

        /* Hide scrollbar */
        -ms-overflow-style: none;  /* IE and Edge */
        scrollbar-width: none;  /* Firefox */
    }
    /* Hide scrollbar for Chrome, Safari and Opera */
    .character-list::-webkit-scrollbar {
        display: none;
    }
    .characterSelected {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        text-transform: uppercase;
        font-size: 8rem;
        animation-name: fade-in-up;
        animation-duration: 0.5s;
    }
    .character-list>li {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        text-transform: uppercase;
        font-size: 4.7rem;
    }
    .character-list>li>a {
        color: #ece6da;
        transition: 0.15s;
        padding: 1rem 0;
    }
    .character-list>li>a:hover {
        margin-left: 0.7rem;
    }
    .character-summary {
        display: flex;
        align-items: center;
    }
    .character-title {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 3rem;
        color: #ece6da;
        animation-name: fade-in-up;
        animation-duration: 0.5s;
    }
    .character-intro {
        font-family: "Nunito Light";
        font-weight: normal;
        font-size: 1rem;
        color: #ece6da;
        animation-name: fade-in-up;
        animation-duration: 0.5s;
    }
    .character-element {
        width: 6rem;
        height: auto;
        margin-top: 0.5rem;
        animation-name: fade-in-up;
        animation-duration: 0.5s;
    }
    @keyframes fade-in-up {
        from { 
            transform: translateY(-1rem);
            opacity: 0;
        };
        to {
            transform: translateY(0);
            opacity: 1;
        };
    }
</style>
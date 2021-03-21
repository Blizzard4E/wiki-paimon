<template>
    <article v-if="canShow" class="container abilities">
        <section>
            <h1>Attack Abilities</h1>
            <div class="abilities-icons-holder">
                <a @click="selectAbility(0)" v-bind:class="{
                    abilityIcon: true,
                    active: currentAbility == 0,
                    characterSelected: true,
                    pyro: selectedChar.element == 'Pyro',
                    anemo: selectedChar.element == 'Anemo',
                    geo: selectedChar.element == 'Geo',
                    hydro: selectedChar.element == 'Hydro',
                    cryo: selectedChar.element == 'Cryo',
                    electro: selectedChar.element == 'Electro',
                    dendro: selectedChar.element == 'Dendro'
                }">
                    <img :src="selectedChar.attackTalents.normalAttack.svg" alt="Ability Icon">
                </a>
                <div class="line">
                    <div></div>
                </div>
                <a @click="selectAbility(1)" v-bind:class="{
                    abilityIcon: true,
                    active: currentAbility == 1,
                    characterSelected: true,
                    pyro: selectedChar.element == 'Pyro',
                    anemo: selectedChar.element == 'Anemo',
                    geo: selectedChar.element == 'Geo',
                    hydro: selectedChar.element == 'Hydro',
                    cryo: selectedChar.element == 'Cryo',
                    electro: selectedChar.element == 'Electro',
                    dendro: selectedChar.element == 'Dendro'
                }">
                    <img :src="selectedChar.attackTalents.skill.svg" alt="Ability Icon">
                </a>
                <div class="line">
                    <div></div>
                </div>
                <a @click="selectAbility(2)" v-bind:class="{
                    abilityIcon: true,
                    active: currentAbility == 2,
                    characterSelected: true,
                    pyro: selectedChar.element == 'Pyro',
                    anemo: selectedChar.element == 'Anemo',
                    geo: selectedChar.element == 'Geo',
                    hydro: selectedChar.element == 'Hydro',
                    cryo: selectedChar.element == 'Cryo',
                    electro: selectedChar.element == 'Electro',
                    dendro: selectedChar.element == 'Dendro'
                }">
                    <img :src="selectedChar.attackTalents.burst.svg" alt="Ability Icon">
                </a>
            </div>
            <div>
                <div v-if="currentAbility==0" class="abilitiesInfo">
                    <h2 >{{selectedChar.attackTalents.normalAttack.title}}</h2>
                    <p v-html="selectedChar.attackTalents.normalAttack.info"></p>
                </div>
            </div>
            <div>
                <div v-if="currentAbility==1" class="abilitiesInfo">
                    <h2>{{selectedChar.attackTalents.skill.title}}</h2>
                    <p v-html="selectedChar.attackTalents.skill.info"></p>
                </div>
            </div>
            <div>
                <div v-if="currentAbility==2" class="abilitiesInfo">
                    <h2>{{selectedChar.attackTalents.burst.title}}</h2>
                    <p v-html="selectedChar.attackTalents.burst.info"></p>
                </div>
            </div>
        </section>
        <section class="abilities-display">
            <div>
                <div v-if="currentAbility==0">
                    <img v-for="gif in selectedChar.attackTalents.normalAttack.gifs" :key="gif.id" :src="gif" v-bind:class="{
                    abilityGif: true,
                    pyro: selectedChar.element == 'Pyro',
                    anemo: selectedChar.element == 'Anemo',
                    geo: selectedChar.element == 'Geo',
                    hydro: selectedChar.element == 'Hydro',
                    cryo: selectedChar.element == 'Cryo',
                    electro: selectedChar.element == 'Electro',
                    dendro: selectedChar.element == 'Dendro'
                }" alt="Abilities Gif Showcase">
                </div>
            </div>
            <div>
                <div v-if="currentAbility==1">
                    <img v-for="gif in selectedChar.attackTalents.skill.gifs" :key="gif.id" :src="gif" v-bind:class="{
                    abilityGif: true,
                    pyro: selectedChar.element == 'Pyro',
                    anemo: selectedChar.element == 'Anemo',
                    geo: selectedChar.element == 'Geo',
                    hydro: selectedChar.element == 'Hydro',
                    cryo: selectedChar.element == 'Cryo',
                    electro: selectedChar.element == 'Electro',
                    dendro: selectedChar.element == 'Dendro'
                }" alt="Abilities Gif Showcase">
                </div>
            </div>
            <div>
                <div v-if="currentAbility==2">
                    <img v-for="gif in selectedChar.attackTalents.burst.gifs" :key="gif.id" :src="gif" v-bind:class="{
                    abilityGif: true,
                    pyro: selectedChar.element == 'Pyro',
                    anemo: selectedChar.element == 'Anemo',
                    geo: selectedChar.element == 'Geo',
                    hydro: selectedChar.element == 'Hydro',
                    cryo: selectedChar.element == 'Cryo',
                    electro: selectedChar.element == 'Electro',
                    dendro: selectedChar.element == 'Dendro'
                }" alt="Abilities Gif Showcase">
                </div>
            </div>
        </section>
    </article>
</template>

<script>
export default {
    props: [
        'selectedChar'
    ],
    data() {
        return {
            canShow: false,
            currentAbility: 0
        }
    },
    watch: {
        selectedChar: function() {
            this.canShow = true
        }
    },
    methods: {
        selectAbility(ability) {
            this.currentAbility = ability
        }
    }
}
</script>

<style scoped>
    .abilities {
        display: grid;
        grid-template-columns: 4fr 3fr;
        margin-top: 3.5rem;
        margin-bottom: 3rem;
    }
    h1 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 3.3rem;
        color: #101520;
        text-transform: uppercase;
    }
    .abilities-icons-holder {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr 1fr 1fr 1fr;
        margin-right: 8rem;
        margin-left: 4rem;
        margin-top: 2rem;
    }
    .line {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .line>div {
        min-width: 100%;
        min-height: 1px;
        background: #101520; 
    }
    .abilityIcon  {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 72px;
        min-width: 72px;
        border: #101520 1px solid;
        transition: 0.2s;
        z-index: 0;
    }
    .abilityIcon.anemo:hover>img, .active.anemo>img {
        filter: invert(100%) sepia(22%) saturate(6010%) hue-rotate(78deg) brightness(99%) contrast(105%);
    }
    .abilityIcon.geo:hover>img, .active.geo>img {
        filter: invert(81%) sepia(73%) saturate(4934%) hue-rotate(0deg) brightness(108%) contrast(103%);
    }
    .abilityIcon.pyro:hover>img, .active.pyro>img {
        filter: invert(36%) sepia(35%) saturate(4266%) hue-rotate(343deg) brightness(110%) contrast(94%);
    }
    .abilityIcon.hydro:hover>img, .active.hydro>img {
        filter: invert(63%) sepia(49%) saturate(5630%) hue-rotate(159deg) brightness(101%) contrast(101%);
    }
    .abilityIcon.cryo:hover>img, .active.cryo>img {
        filter: invert(95%) sepia(73%) saturate(1039%) hue-rotate(149deg) brightness(106%) contrast(105%);
    }
    .abilityIcon.electro:hover>img, .active.electro>img {
        filter: invert(71%) sepia(27%) saturate(1008%) hue-rotate(210deg) brightness(106%) contrast(106%);
    }
    .abilityIcon.dendro:hover>img, .active.dendro>img {
        filter: invert(83%) sepia(22%) saturate(1533%) hue-rotate(25deg) brightness(109%) contrast(82%);
    }
    .abilityIcon:hover, .active {
        background: #101520; 
    }
    .abilityIcon>img {
        width: 47px;
        height: 47px;
        filter: invert(5%) sepia(42%) saturate(802%) hue-rotate(183deg) brightness(97%) contrast(94%);
    }
    .abilitiesInfo {
        max-width: 30rem;
        margin-left: 4rem;
        margin-top: 1.5rem;
        animation: fade-in-up;
        animation-duration: 0.2s;
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
    h2 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 2rem;
        text-transform: uppercase;
        color: #101520;
    }
    p {
        font-family: "Nunito Light";
        font-weight: normal;
        font-size: 1rem;
        color: #101520;
    }
    p >>> .ability-ref {
        color: #ece6da;
    }
    p >>> span {
        font-family: "Nunito Bold";
        font-weight: normal;
        font-size: 1rem;
        background: #101520;
        padding: 0 0.2rem;
    }
    p >>> h3 {
        font-family: 'Nunito Bold';
        font-weight: normal;
        font-size: 1.2rem;
        text-transform: capitalize;
        margin-top: 0.6rem;
        color: #101520;
    }
    .abilities-display {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
    }
    .abilityGif {
        width: 500px;
        height: auto;
        padding: 2px;
        border: #101520 0.5rem solid;
        margin: 0.25rem 0;
        animation-name: fade-in-up;
        animation-duration: 0.2s;
    }
    .abilityGif.anemo {
        background: #38FFBD;
    }
    .abilityGif.geo {
        background: #FFCC00;
    }
    .abilityGif.pyro {
        background: #F84F38;
    }
</style>
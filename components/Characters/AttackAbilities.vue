<template>
    <div class="background">
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
            </section>
        </article>
    </div>
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
            this.canShow = true,
            this.currentAbility = 0;
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
        padding-top: 3.5rem;
    }
    h1 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 3.3rem;
        color: #101520;
        text-transform: uppercase;
        margin-left: 1rem;
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
        filter: invert(73%) sepia(41%) saturate(6341%) hue-rotate(146deg) brightness(102%) contrast(101%);
    }
    .abilityIcon.cryo:hover>img, .active.cryo>img {
        filter: invert(76%) sepia(32%) saturate(885%) hue-rotate(145deg) brightness(106%) contrast(99%);
    }
    .abilityIcon.electro:hover>img, .active.electro>img {
        filter: invert(39%) sepia(71%) saturate(875%) hue-rotate(234deg) brightness(104%) contrast(103%);
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
    .abilities-display>div {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
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
    .abilityGif.hydro {
        background: #00CBEA;
    }
    .abilityGif.cryo {
        background: #4EF3FE;
    }
    .abilityGif.electro {
        background: #B15DFF;
    }
    @media only screen and (max-width: 599.98px) {
        section {
            min-width: 100%;
        }
        .abilities-icons-holder {
            margin-left: 1rem;
        }
        .abilities {
            grid-template-columns: 1fr;
            margin-top: 1rem;
        }
        .abilityGif {
            margin-top: 2rem;
            width: 280px;
        }
        .abilitiesInfo {
            max-width: 14rem;
            margin-left: 1rem;
        }
        h1 {
            font-size: 3.1rem;
        }
        p >>> h3 {
            font-size: 1.25rem;
        }
        .abilityIcon {
            min-width: 56px;
            min-height: 56px;
        }
        .abilityIcon>img {
            width: 32px;
            height: 32px;
        }
    }

    @media (min-width: 600px) and (max-width: 767.98px) {
        .abilities-icons-holder {
            margin-left: 1rem;
        }
        .abilities {
            grid-template-columns: 1fr;
        }
        .abilityGif {
            margin-top: 2rem;
        }
    }

    @media (min-width: 768px) and (max-width: 991.98px) {
        .abilities {
            grid-template-columns: 1fr;
        }
        .abilityGif {
            margin-top: 2rem;
        }
        h2 {
            font-size: 1.8rem;
        }
        p >>> h3 {
            font-size: 1.1rem;
        }
        .abilityIcon {
            min-width: 64px;
            min-height: 64px;
        }
        .abilityIcon>img {
            width: 36px;
            height: 36px;
        }
    }

    @media (min-width: 992px) and (max-width: 1299.98px) {
        .abilityGif {
            width: 380px;
        }
        h1 {
            margin-left: 0;
        }
    }

    @media only screen and (min-width: 1300px) {
        h1 {
            margin-left: 0;
        }
    }
</style>
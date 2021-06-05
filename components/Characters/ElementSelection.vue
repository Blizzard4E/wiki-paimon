<template>
    <article v-if="canShow" class="container elements">
        <section>
            <h1>Elements</h1>
            <div class="elements-icons-holder">
                <div class="element">
                    <a @click="selectElement('anemo')" v-bind:class="{
                        elementIcon: true,
                        active: currentElement == 'anemo',
                        anemo: true
                    }">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622685165/Wiki%20Paimon/Elements%20Icon/Anemo_Icon_ryhcz5.svg" alt="Element Icon">
                    </a>
                    <div class="line">
                        <div></div>
                    </div>
                </div>
                <div class="element">
                    <a @click="selectElement('geo')" v-bind:class="{
                        elementIcon: true,
                        active: currentElement == 'geo',
                        geo: true
                    }">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622685165/Wiki%20Paimon/Elements%20Icon/Geo_Icon_vssgtb.svg" alt="Element Icon">
                    </a>
                    <div class="line">
                        <div></div>
                    </div>
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
            currentElement: 'anemo',
            selectedCharElement: {},
            currentCharName: ''
        }
    },
    watch: {
        selectedChar: function(value) {
            this.canShow = true
            if(value.name != this.currentCharName)
            {
                this.currentElement = 'anemo'
            }
        }
    },
    methods: {
        async selectElement(element) {
            this.currentElement = element;
            this.currentCharName = this.selectedChar.name;
            let charName = this.selectedChar;
            charName = charName.name.toLowerCase();
            let newSelectedChar = await import(`../../data/characters/${charName}_${this.currentElement}.json`);
            this.selectedCharElement = newSelectedChar;
            //Update Selected Character For Parents
            this.$emit('update-selected-char', this.selectedCharElement);
        },
        CheckElement()
        {
            this.currentElement = this.selectedChar.element;
        }
    }
}
</script>

<style scoped>
    .elements {
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
    .elements-icons-holder {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        margin-right: 8rem;
        margin-left: 4rem;
        margin-top: 2rem;
    }
    .element {
        display: grid;
        grid-template-columns: 1fr 1fr;
        margin-bottom: 1rem;
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
    .element:nth-child(4n) > .line, .element:last-child > .line {
        display: none;
    }
    .elementIcon  {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 72px;
        min-width: 72px;
        border: #101520 1px solid;
        transition: 0.2s;
        z-index: 0;
    }
    .elementIcon.anemo:hover>img, .active.anemo>img {
        filter: invert(100%) sepia(22%) saturate(6010%) hue-rotate(78deg) brightness(99%) contrast(105%);
    }
    .elementIcon.geo:hover>img, .active.geo>img {
        filter: invert(81%) sepia(73%) saturate(4934%) hue-rotate(0deg) brightness(108%) contrast(103%);
    }
    .elementIcon.pyro:hover>img, .active.pyro>img {
        filter: invert(36%) sepia(35%) saturate(4266%) hue-rotate(343deg) brightness(110%) contrast(94%);
    }
    .elementIcon.hydro:hover>img, .active.hydro>img {
        filter: invert(73%) sepia(41%) saturate(6341%) hue-rotate(146deg) brightness(102%) contrast(101%);
    }
    .elementIcon.cryo:hover>img, .active.cryo>img {
        filter: invert(76%) sepia(32%) saturate(885%) hue-rotate(145deg) brightness(106%) contrast(99%);
    }
    .elementIcon.electro:hover>img, .active.electro>img {
        filter: invert(39%) sepia(71%) saturate(875%) hue-rotate(234deg) brightness(104%) contrast(103%);
    }
    .elementIcon.dendro:hover>img, .active.dendro>img {
        filter: invert(83%) sepia(22%) saturate(1533%) hue-rotate(25deg) brightness(109%) contrast(82%);
    }
    .elementIcon:hover, .active {
        background: #101520; 
    }
    .elementIcon>img {
        width: 47px;
        height: 47px;
        filter: invert(5%) sepia(42%) saturate(802%) hue-rotate(183deg) brightness(97%) contrast(94%);
    }
    .elementsInfo {
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
    p >>> .element-ref {
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
    .elements-display>div {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
    }
    .elementGif {
        width: 500px;
        height: auto;
        padding: 2px;
        border: #101520 0.5rem solid;
        margin: 0.25rem 0;
        animation-name: fade-in-up;
        animation-duration: 0.2s;
    }
    .elementGif.anemo {
        background: #38FFBD;
    }
    .elementGif.geo {
        background: #FFCC00;
    }
    .elementGif.pyro {
        background: #F84F38;
    }
    .elementGif.hydro {
        background: #00CBEA;
    }
    .elementGif.cryo {
        background: #4EF3FE;
    }
    .elementGif.electro {
        background: #B15DFF;
    }
    @media only screen and (max-width: 599.98px) {
        .elements-icons-holder {
            margin-left: 1rem;
        }
        section {
            min-width: 100%;
        }
        .elements {
            grid-template-columns: 1fr;
            margin-top: 1rem;
        }
        .elementGif {
            margin-top: 2rem;
            width: 280px;
        }
        .elementsInfo {
            max-width: 14rem;
            margin-left: 1rem;
        }
        h1 {
            font-size: 3.1rem;
        }
        p >>> h3 {
            font-size: 1.25rem;
        }
        .elementIcon {
            min-width: 56px;
            min-height: 56px;
        }
        .elementIcon>img {
            width: 32px;
            height: 32px;
        }
    }

    @media (min-width: 600px) and (max-width: 767.98px) {
        .elements-icons-holder {
            margin-left: 1rem;
        }
        .elements {
            grid-template-columns: 1fr;
        }
        .elementGif {
            margin-top: 2rem;
        }
    }

    @media (min-width: 768px) and (max-width: 991.98px) {
        .elements {
            grid-template-columns: 1fr;
        }
        .elementGif {
            margin-top: 2rem;
        }
        h2 {
            font-size: 1.8rem;
        }
        p >>> h3 {
            font-size: 1.1rem;
        }
        .elementIcon {
            min-width: 64px;
            min-height: 64px;
        }
        .elementIcon>img {
            width: 36px;
            height: 36px;
        }
    }

    @media (min-width: 992px) and (max-width: 1299.98px) {
        .elementGif {
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
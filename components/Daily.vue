<template>
    <div class="background">
       <div class="container">
           <article>
               <h1>Monday | Thursday | Sunday</h1>
               <section>
                    <h2>Talent Books</h2>
                    <div>
                        <a v-for="book in talentBooks.Monday_Thursday_Sunday" :key="book.id" class="item-holder">
                            <div class="mat">
                                <img class="green" :src="book.variety[0]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="blue" :src="book.variety[1]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="purple" :src="book.variety[2]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                        </a>
                    </div>
                </section>
                <section>
                    <h2>Weapon Ascension</h2>
                    <div>
                        <a v-for="mat in weaponMats.Monday_Thursday_Sunday" :key="mat.id" class="item-holder">
                            <div class="mat">
                                <img class="green" :src="mat.variety[0]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="blue" :src="mat.variety[1]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="purple" :src="mat.variety[2]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="gold" :src="mat.variety[3]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                        </a>
                    </div>
                </section>
           </article>
           <article>
               <h1>Tuesday | Friday | Sunday</h1>
               <section>
                    <h2>Talent Books</h2>
                    <div>
                        <a v-for="book in talentBooks.Tuesday_Friday_Sunday" :key="book.id" class="item-holder">
                            <div class="mat">
                                <img class="green" :src="book.variety[0]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="blue" :src="book.variety[1]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="purple" :src="book.variety[2]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                        </a>
                    </div>
                </section>
                <section>
                    <h2>Weapon Ascension</h2>
                    <div>
                        <a v-for="mat in weaponMats.Tuesday_Friday_Sunday" :key="mat.id" class="item-holder">
                            <div class="mat">
                                <img class="green" :src="mat.variety[0]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="blue" :src="mat.variety[1]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="purple" :src="mat.variety[2]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="gold" :src="mat.variety[3]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                        </a>
                    </div>
                </section>
           </article>
           <article>
               <h1>Wednesday | Saturday | Sunday</h1>
               <section>
                    <h2>Talent Books</h2>
                    <div>
                        <a v-for="book in talentBooks.Wednesday_Saturday_Sunday" :key="book.id" class="item-holder">
                            <div class="mat">
                                <img class="green" :src="book.variety[0]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="blue" :src="book.variety[1]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="purple" :src="book.variety[2]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                        </a>
                    </div>
                </section>
                <section>
                    <h2>Weapon Ascension</h2>
                    <div>
                        <a v-for="mat in weaponMats.Wednesday_Saturday_Sunday" :key="mat.id" class="item-holder">
                            <div class="mat">
                                <img class="green" :src="mat.variety[0]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="blue" :src="mat.variety[1]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="purple" :src="mat.variety[2]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                            <div class="mat">
                                <img class="gold" :src="mat.variety[3]">
                                <div class="line">
                                    <div></div>
                                </div>
                            </div>
                        </a>
                    </div>
                </section>
           </article>
       </div>
    </div>
</template>

<script>
import TALENT_BOOKS from '../data/talent_books';
import WEAPON_MATERIALS from '../data/weapon_materials';

export default {
    data() {
        return {
            talentBooks: '',
            weaponMats: ''
        }
    },
    mounted() {
        this.talentBooks = TALENT_BOOKS;
        this.weaponMats = WEAPON_MATERIALS;
    }
}
</script>

<style scoped>
    .mat {
        display: grid;
        grid-template-columns: 1fr 1fr;
        margin-bottom: 1rem;
    }
    .green {
        background: #38FFBD;
    }
    .blue {
        background: #00CBEA;
    }
    .purple {
        background: #B15DFF;
    }
    .gold {
        background: #FFCC00;
    }
    .background {
        background: #ece6da;
    }
    .item-holder {
        display: grid;
        grid-template-columns: 1fr 1fr 1fr 1fr;
        margin-top: 1rem;
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
    .mat:nth-child(4n) > .line, .mat:last-child > .line {
        display: none;
    }
    a {
        display: block;
    }
    p {
        font-family: "Nunito Light";
        font-weight: normal;
        font-size: 1.2rem;
        color: #101520;
    }
    section {
        margin-top: 1rem;
        margin-left: 4rem;
        display: flex;
        align-items: center;
    }
    img {
        border: #101520 solid 1px;
        width: 64px;
        height: auto;
        image-rendering:-moz-crisp-edges;          /* Firefox        */
        image-rendering:-o-crisp-edges;            /* Opera          */
        image-rendering:-webkit-optimize-contrast; /* Safari         */
        image-rendering:optimize-contrast;         /* CSS3 Proposed  */
    }
    h1 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 3.3rem;
        color: #101520;
        text-transform: uppercase;
        margin-left: 1rem;
        padding-top: 1rem;
    }
    h2 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 2rem;
        text-transform: uppercase;
        color: #101520;
        margin-right: 2rem;
    }
    @media only screen and (max-width: 599.98px) {
        h1 {
            font-size: 1.5rem;
        }
        h2 {
            font-size: 1.2rem;
        }
        img {
            width: 48px;
        }
        section {
            flex-wrap: wrap;
            margin-left: 2rem;
        }
    }

    @media (min-width: 600px) and (max-width: 767.98px) {

    }

    @media (min-width: 768px) and (max-width: 991.98px) {

    }

    @media (min-width: 992px) and (max-width: 1199.98px) {

    }

    @media only screen and (min-width: 1200px) {

    }
</style>
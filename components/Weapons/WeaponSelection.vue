<template>
    <div class="container">
        <section>
            <h1>Weapons</h1>
            <ul>
                <li v-bind:class="{
                    active: weapon.name == selectedWeapon
                }" v-for="weapon in weaponsList" @click="SelectWeapon(weapon.name)" :key="weapon.id">
                    <div>
                        <img v-bind:class="{
                            blue: weapon.rarity == 3,
                            purple: weapon.rarity == 4,
                            gold: weapon.rarity == 5
                        }" :src="weapon.img[0]">
                    </div>
                    <h2>{{weapon.name}}</h2>
                </li>
            </ul>
        </section>
    </div>
</template>

<script>
import axios from 'axios'
import weaponsList from '../../data/weapons';

export default {
    data() { 
        return {
            weaponsList: '',
            selectedWeapon: ''
        }
    },
    methods: {
        SelectWeapon(weapon) {
            this.selectedWeapon = weapon;

            //Update Selected Weapon For Parents
            this.$emit('update-selected-weap', this.selectedWeapon);
        },
        GetWeapons() {
            this.weaponsList = this.weaponsList.sort(this.CompareName);
            this.weaponsList = this.weaponsList.sort(this.CompareRarity);
        },
        CompareName(a, b) {
            if (a.name < b.name){
                return -1;
            }
            if (a.name > b.name){
                return 1;
            }
            return 0;
        },
        CompareRarity(a, b) {
            if (a.rarity < b.rarity){
                return 1;
            }
            if (a.rarity > b.rarity){
                return -1;
            }
            return 0;
        }
    },
    mounted() {
        this.weaponsList = weaponsList;
        this.GetWeapons();
        this.SelectWeapon('Engulfing Lightning');
    }
}
</script>

<style scoped>
    .blue {
        background: #00CBEA;
    }
    .purple {
        background: #B15DFF;
    }
    .gold {
        background: #FFCC00;
    }

    h1 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 3.3rem;
        color: #101520;
        text-transform: uppercase;
        margin-left: 1rem;
        padding-top: 2rem;
        padding-bottom: 1rem;
    }

    ul {
        max-height: 30rem;
        overflow-y: scroll;
        overflow-x: visible;
        scroll-snap-align: center;
        transition: 0.3s;
        /* Hide scrollbar */
        -ms-overflow-style: none;  /* IE and Edge */
        scrollbar-width: none;  /* Firefox */
        display: grid;
        grid-template-columns: 1fr 1fr 1fr;
        flex-wrap: wrap;
    }
    /* Hide scrollbar for Chrome, Safari and Opera */
    ul::-webkit-scrollbar {
        display: none;
    }
    
    li {
        display: flex;
        align-items: center;
        padding: 0.6rem;
        margin: 0.4rem;
        transition: 0.3s;
    }
    li:hover, .active {
        background: #101520;
    }

    h2 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 1.5rem;
        color: #101520;
        text-transform: uppercase;
        margin-left: 1rem;
        transition: 0.3s;
    }
    li:hover > h2, .active > h2 {
        color: #ece6da;
        margin-top: -1.5rem;
        font-size: 1.6rem;
    }

    li > div {
        min-width: 100px;
        min-height: 100px;
        overflow: hidden;
    }
    img {
        border: #101520 solid 1px;
        width: 100px;
        height: 100px;
        transition: 0.3s;
    }
    li:hover > div > img, .active > div > img{
        transform: scale(1.3);
    }
    @media only screen and (max-width: 599.98px) {
        ul {
            grid-template-columns: 1fr;
        }
        h1 {
            padding-top: 1rem;
            padding-bottom: 0rem;
            font-size: 3rem;
        }
    }

    @media (min-width: 600px) and (max-width: 767.98px) {
        ul {
            grid-template-columns: 1fr;
        }
        h1 {
            padding-top: 1rem;
            padding-bottom: 0rem;
            font-size: 3rem;
        }
    }

    @media (min-width: 768px) and (max-width: 991.98px) {
        ul {
            grid-template-columns: 1fr 1fr;
        }
        h1 {
            padding-top: 1rem;
            padding-bottom: 0rem;
            font-size: 3.1rem;
        }
    }

    @media (min-width: 992px) and (max-width: 1199.98px) {

    }

    @media only screen and (min-width: 1200px) {

    }
</style>
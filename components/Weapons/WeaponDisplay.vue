<template>
    <main class="container" v-if="canShow">
        <div class="weapon-display">
            <section class="weap-img-display">
                <img :src="currentWeapon.img[1]" alt="">
            </section>
            <section class="weapon-stats">
                <h1 class="weapon-name">{{currentWeapon.name}}</h1>
                <div class="line"></div>
                <div class="weapon-stat">{{currentWeapon.baseAtk[0]}} - {{currentWeapon.baseAtk[1]}} ATK</div>
                <div class="line"></div>
                <div class="weapon-stat">{{currentWeapon.baseStat[0]}} - {{currentWeapon.baseStat[1]}} {{currentWeapon.baseStat[2]}}</div>
                <div class="line"></div>
                <h2 class="weapon-effect-name">{{currentWeapon.passive[0]}}</h2>
                <p class="weapon-effect-info">{{currentWeapon.passive[1]}}</p>
            </section>
        </div>
    </main>
</template>

<script>
import axios from 'axios'
import weaponsList from '../../data/weapons';

export default {
    props: ['selectedWeapon'],
    data() {
        return {
            canShow: false,
            weaponsList: '',
            currentWeapon: ''
        }
    },
    watch: {
        selectedWeapon: function(value) {
            this.SelectWeapon(value);
        }
    },
    methods: {
        SelectWeapon(weaponName) {
            this.weaponsList = weaponsList;
            console.log(this.weaponsList);
            for(let i=0; i<this.weaponsList.length; i++)
            {
                if(this.weaponsList[i].name == weaponName){
                    this.currentWeapon = this.weaponsList[i];
                }
            }
            this.canShow = true;
        }
    }
}
</script>

<style scoped>
    .weapon-display {
        display: grid;
        grid-template-columns: 3fr 2fr;
        margin-bottom: 1rem;
    }

    .weapon-stats {
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

    .weapon-name {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 3rem;
        color: #ece6da;
        text-align: center;
        margin: 1rem;
    }

    .weapon-stat {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 2.2rem;
        color: #ece6da;
        text-align: center;
        margin: 1rem;
    }

    .weapon-effect-name {
        font-family: 'Nunito Light';
        font-weight: bold;
        font-size: 1.3rem;
        color: #ece6da;
        margin: 1rem 1rem 0.5rem 1rem;
    }

    .weapon-effect-info {
        font-family: 'Nunito Light';
        font-weight: normal;
        font-size: 1rem;
        color: #ece6da;
        margin: 0 1rem;
    }

    .line {
        min-width: 100%;
        min-height: 1px;
        background: #ece6da;
    }

    .weap-img-display {
        display: flex;
        justify-content: center;
    }
    img {
        height: 500px;
        width: auto;
        animation: moving 5s linear infinite 0.5s, scale-up 0.2s linear;
    }
    @keyframes moving {
        0% {transform: translateY(0px);}
        25% {transform: translateY(-6px);}
        50% {transform: translateY(6px);}
        75% {transform: translateY(-6px);}
        100% {transform: translateY(0px);}
    }

    @media only screen and (max-width: 599.98px) {
        .weapon-display {
            grid-template-columns: 1fr;
        }
        img {
            height: 240px;
        }
        .weapon-stats {
            margin: 1rem;
        }
        .weapon-name {
            font-size: 2rem;
            margin: 0.5rem;
        }
        .weapon-stat {
            font-size: 1.8rem;
            margin: 0.5rem;
        }
        .weapon-effect-name {
            font-size: 1.2rem;
            margin-top: 0.5rem;
            margin-bottom: 0.25rem;
        }
        .weapon-effect-info {
            margin: 1 0.5rem;
        }
    }

    @media (min-width: 600px) and (max-width: 767.98px) {
        .weapon-display {
            grid-template-columns: 1fr;
        }
        img {
            height: 260px;
        }
        .weapon-stats {
            margin: 1rem;
        }
        .weapon-name {
            font-size: 2rem;
            margin: 0.5rem;
        }
        .weapon-stat {
            font-size: 1.8rem;
            margin: 0.5rem;
        }
        .weapon-effect-name {
            font-size: 1.2rem;
            margin-top: 0.5rem;
            margin-bottom: 0.25rem;
        }
        .weapon-effect-info {
            margin: 1 0.5rem;
        }
    }

    @media (min-width: 768px) and (max-width: 991.98px) {
        .weapon-display {
            grid-template-columns: 1fr 1fr;
        }
        img {
            height: 360px;
        }
    }

    @media (min-width: 992px) and (max-width: 1199.98px) {
        img {
            height: 400px;
        }
    }

    @media only screen and (min-width: 1200px) {

    }
</style>
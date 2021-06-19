<template>
    <div>
        <div class="dt sd container">
            <header>
                <section class="logo-section">
                    <img class="logo" src="https://res.cloudinary.com/duzvevuup/image/upload/v1622903672/Wiki%20Paimon/Logos/wiki_paimon_logo_qdnr2k.png">
                    <h1>Wiki Paimon</h1>
                </section>
                <nav>
                    <a @click="selectTab(0)" :class="{active: currentTab == 0}">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622899748/Wiki%20Paimon/Icons/Resin_mk9abh.svg" alt="Rein Usages">
                    </a>
                    <a @click="selectTab(1)" :class="{active: currentTab == 1}">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622899749/Wiki%20Paimon/Icons/Profile_hxaybe.svg" alt="Characters">
                    </a>
                    <a @click="selectTab(2)" :class="{active: currentTab == 2}">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622899749/Wiki%20Paimon/Icons/Weapon_wv7xxi.svg" alt="Weapons">
                    </a>
                </nav>
            </header>
        </div>
        <div class="mb pb tb">
            <header>
                <section class="logo-section">
                    <img class="logo" src="https://res.cloudinary.com/duzvevuup/image/upload/v1622903672/Wiki%20Paimon/Logos/wiki_paimon_logo_qdnr2k.png">
                    <h1>Wiki Paimon</h1>
                </section>
                <nav>
                    <a @click="selectTab(0)" :class="{active: currentTab == 0}">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622899748/Wiki%20Paimon/Icons/Resin_mk9abh.svg" alt="Rein Usages">
                    </a>
                    <a @click="selectTab(1)" :class="{active: currentTab == 1}">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622899749/Wiki%20Paimon/Icons/Profile_hxaybe.svg" alt="Characters">
                    </a>
                    <a @click="selectTab(2)" :class="{active: currentTab == 2}">
                        <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1622899749/Wiki%20Paimon/Icons/Weapon_wv7xxi.svg" alt="Weapons">
                    </a>
                </nav>
            </header>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            currentTab: 0
        }
    },
    methods: {
        selectTab(tab)
        {
            this.currentTab = tab;
            //Update Tab Tab For Parents
            this.$emit('update-selected-tab', this.currentTab);
        }
    },
    mounted()
    {
        this.selectTab(2);
    }
}
</script>

<style scoped>
    nav {
        display: flex;
        align-items: center;
    }
    .active > img, a:hover>img{
        filter: invert(100%) sepia(100%) saturate(0%) hue-rotate(307deg) brightness(109%) contrast(102%);
        transform: scale(1.1);
    }
    a {
        padding: 1rem;
        transition: 0.2s;
    }
    a > img {
        width: 32px;
        filter: invert(54%) sepia(0%) saturate(0%) hue-rotate(188deg) brightness(92%) contrast(83%);
        transition: 0.2s;
    }
    header {
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 1.5rem 0;
        animation-name: fade-in-up;
        animation-duration: 0.5s;
        overflow-y: hidden;
        margin-left: 1rem;
    }
    .logo-section {
        display: flex;
        align-items: center;
    }
    .logo {
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
        font-size: 2.8rem;
        color: #FEFEFE;
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
    @media only screen and (max-width: 599.98px) {
        a {
            padding: 0.5rem;
        }
        a > img {
            width: 24px;
        }
        header {
            display: block;
            padding: 1rem 0;
        }
        h1 {
            font-size: 2rem;
        }
        .logo {
            width: 52px;
        }
        .logo-section {
            justify-content: center;
            margin-bottom: 1rem;
        }
        nav {
            justify-content: space-around;
        }
    }

    @media (min-width: 600px) and (max-width: 767.98px) {
        a {
            padding: 0.5rem;
        }
        a > img {
            width: 24px;
        }
        header {
            display: block;
            padding: 1rem 0;
        }
        h1 {
            font-size: 2rem;
        }
        .logo {
            width: 52px;
        }
        .logo-section {
            justify-content: center;
            margin-bottom: 1rem;
        }
        nav {
            justify-content: space-around;
        }
    }

    @media (min-width: 768px) and (max-width: 991.98px) {
        
    }

    @media (min-width: 992px) and (max-width: 1199.98px) {
        
    }

    @media only screen and (min-width: 1200px) {

    }
</style>
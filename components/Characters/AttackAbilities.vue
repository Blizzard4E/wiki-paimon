<template>
    <article class="container attack-abilities">
        <section class="abilities">
            <h1>Attack Abilities</h1>
            <div class="abilities-icons-holder">
                <div class="ability-icon active">
                    <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1615555817/Wiki%20Paimon/Weapon%20Styles/Spear_Weapon_m4fybb.svg" alt="Ability Icon">
                </div>
                <div class="line">
                    <div></div>
                </div>
                <div class="ability-icon">
                    <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1615555903/Wiki%20Paimon/Characters/Xiao/Talent_Lemniscatic_Wind_Cycling_ryrhsf.svg" alt="Ability Icon">
                </div>
                <div class="line">
                    <div></div>
                </div>
                <div class="ability-icon">
                    <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1615555903/Wiki%20Paimon/Characters/Xiao/Talent_Bane_of_All_Evil_jw9kbx.svg" alt="Ability Icon">
                </div>
            </div>
            <div class="abilities-info">
                <h2>Ability Name</h2>
                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Eaque hic iusto dolor iure voluptatibus doloribus, totam recusandae minus sint voluptatum eius non architecto illum harum alias molestias! Porro, excepturi nam.</p>
            </div>
        </section>
        <section class="attack-abilities-display">
            <figure class="attack-abilities-gif">
                <img src="https://res.cloudinary.com/duzvevuup/image/upload/v1615285868/Wiki%20Paimon/Characters/Xiao/Talent_Xiao_Whirlwind_Thrust_Sequence_pr2x7l.gif" alt="Abilities Gif Showcase">
                <div class="display-line"></div>
            </figure>
            <caption>Showcase</caption>
        </section>
    </article>
</template>

<script>
export default {

}
</script>

<style scoped>
    .attack-abilities {
        display: grid;
        grid-template-columns: 4fr 3fr;
        margin-top: 3.5rem;
        margin-bottom: 5rem;
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
    .ability-icon  {
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 72px;
        min-width: 72px;
        border: #101520 1px solid;
    }
    .ability-icon:hover, .active {
        background: #101520; 
        transition: 0.2s;
    }
    .ability-icon:hover>img, .active>img {
        filter: invert(100%) sepia(19%) saturate(6082%) hue-rotate(76deg) brightness(107%) contrast(98%);
        transition: 0.2s;
    }
    .ability-icon>img {
        width: 47px;
        height: auto;
    }
    .abilities-info {
        max-width: 30rem;
        margin-left: 4rem;
        margin-top: 1.5rem;
    }
    h2 {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 2rem;
        text-transform: uppercase;
    }
    p {
        font-family: "Nunito Light";
        font-weight: normal;
        font-size: 1rem;
    }
    .attack-abilities-display {
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        align-items: center;
    }
    .attack-abilities-gif {
        max-width: 500px;
        height: auto;
    }
    .attack-abilities-gif>img {
        width: 100%;
        height: auto;
        border-left: #38FFBD 1rem solid;
    }
    .display-line {
        background: #101520;
        min-width: 100%;
        min-height: 1rem;
        margin-top: -0.25rem;
        border-left: #ece6da 1rem solid;
    }
    caption {
        font-family: 'Big Shoulders Display';
        font-weight: normal;
        font-size: 1.5rem;
        text-transform: uppercase;
        display: flex;
        align-self: center;
    }
</style>
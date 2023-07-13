<script>
    import { cards } from "src/ts/cards";
</script>

<section>
    <h2 class="h2">Производители дисков</h2>
    <div class="cards-container">
        {#each cards  as card}
                <a href={card.url} class="card">
                    <img class="logo" src={card.logoSrc} alt={card.url}>
                    <button class="watch-all-button">Посмотреть все</button>
                <img class="disk-image" src={card.imageSrc} alt={card.url}></a>
        {/each}
    </div>
</section>

<style lang="scss">
    @import '../../styles/variables.scss';

    section {
        margin-top: 60px;
        width: 100%;
        background: transparent;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .h2 {
        font-size: 2rem;
        letter-spacing: 0.7px;
        font-weight: 600;
        color: #333;
        text-align: center;
        margin: 15px 0;

        @media (max-width: 600px) {
            font-size:  .875rem;
            letter-spacing: 0.5px;
        }
    }

    .cards-container {
        display: flex;
        flex-direction: row;
        align-items: stretch;
        justify-content: space-between;
        flex-wrap: wrap;
        gap: 10px;
        width: 100%;
        max-width: 64rem;

        @media (max-width: 1000px) {
            width: 740px;
            gap: 10px;
        }
        @media (max-width: 600px) {
            width: 100%;
            align-items: center;
            justify-content: flex-start;
        }
    }

    .card {
        border-radius: 0.25rem;
        box-shadow: 0 2px 4px 0 rgba(81, 115 ,152, .2);
        overflow: hidden;
        background-color: $white;
        width: 14.75rem;
        height: 16.25rem;
        padding-top: 0.75rem;
        padding-left: 0;
        position: relative;
        text-decoration: none;
        display: flex;
        flex-direction: column;
        align-items: center;

        @media (max-width: 1000px) {
            width: 22.625rem;
        }
        @media (max-width: 600px) {
            width: 22rem;
        }
    }

    .logo {
        width: 100%;
        height: 2.625rem;
        margin-top: 0;
        object-fit: contain;
        position: relative;
        z-index: 1;
        zoom: 75%;

        @media (max-width: 1000px) {
            max-width: 180px;
        }
        @media (max-width: 600px) {
            max-width: 140px;
        }
    }

    .watch-all-button {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        flex-wrap: wrap;
        border-radius: .125rem;
        width: 11.25rem;
        height: 2.25rem;
        margin-top: 10px;
        position: relative;
        z-index: 1;
        background-color: transparent;
        transition: .3s ease-in-out;
        border: none;
        outline: none;
        text-decoration: none;


        &:hover {
            background-color: #ebf0f5;
        }
    }

    .disk-image {
        position: absolute;
        right: -5px;
        bottom:-1px;
        width: 11.5rem;
        height: 9.5rem;
        margin-top: .875rem;
        object-fit: contain;
    }

</style>
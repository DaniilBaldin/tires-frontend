<script>
    import { onMount } from 'svelte';
    import axios from 'axios';

    const endpoint = import.meta.env.PUBLIC_BASE_URL;
    let disk = [];

    onMount(async function () {
        const response = await axios.get(`${endpoint}rims`);
        const data = response.data;
        disk = data.slice(0, 12);
    });
</script>

<section>
    <div class="container">
        <h2 class="title">Популярные модели</h2>
        <div>
            <div class="cards-wrapper">
                {#each disk as disk}
                    <a
                        href={`disk/${disk.id}`}
                        class="card"
                    >
                        <img
                            class="card_image"
                            src={`${endpoint}images/${disk.thumbnail}`}
                            alt=""
                        />
                        <p class="card_name">{disk.brandName} - {disk.modelName}</p>
                        <p class="card_price">от {(disk.priceToShow * 36.6).toFixed(0)} грн.</p>
                        <p class="card_subtitle">⌀{disk.configs[0].diameter}''</p>
                        <div
                            class="button_container"
                            style="padding-right:12px; margin-top: 10px"
                        >
                            <a
                                class="card_button"
                                href={`/disk/${disk.id}`}>Заказать</a
                            >
                        </div>
                    </a>
                {/each}
            </div>
            <div class="button_container">
                <a
                    href="disks"
                    class="show-more_button">Показать больше</a
                >
            </div>
        </div>
    </div>
</section>

<style lang="scss">
    @import '../../styles/variables.scss';

    section {
        margin-top: 0rem;
        width: 100%;
        background: transparent;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .container {
        width: 100%;
        max-width: 64rem;
        margin: 0 auto;
        padding: 0 1rem;
    }

    .title {
        font-size: 2rem;
        letter-spacing: 0.7px;
        font-weight: 500;
        color: #333;
        text-align: center;
        margin: 15px 0;
    }

    .cards-wrapper {
        width: 100%;
        margin: 0.75rem auto;
        display: flex;
        flex-flow: row wrap;
        justify-content: center;
        justify-content: space-between;
        /* gap: 25px; */
        /* flex-direction: row;
        align-items: stretch;
        flex-wrap: wrap; */
    }

    .card {
        display: flex;
        flex-direction: column;
        align-items: stretch;
        justify-content: flex-start;
        flex-wrap: wrap;
        width: 14.75rem;
        height: 22.125rem;
        padding: 0 0 0.75rem 0.75rem;
        cursor: pointer;
        text-decoration: none;
        border: none;
        outline: none;
        background-color: $white;
        margin-bottom: 20px;
        border-radius: 0.25rem;
        box-shadow: 0 2px 4px 0 rgba(81, 115, 152, 0.2);
        overflow: hidden;
    }

    .card_image {
        height: 14.7rem;
        width: 14.7rem;
        margin-left: -12px;
        object-fit: contain;
    }

    .card_name {
        margin: 0;
        margin-top: 8px;
        font-size: 15px;
        white-space: nowrap;
        text-overflow: ellipsis;
        overflow: hidden;
        color: #507299;
        letter-spacing: 0.5px;
        text-align: left;
    }

    .card_price {
        margin: 0;
        margin-top: 0.25rem;
        font-size: 15px;
        font-weight: 700;
        color: $black;
        letter-spacing: 0.5px;
    }

    .card_subtitle {
        margin: 0;
        margin-top: 0.25rem;
        font-size: 0.625rem;
        color: grey;
        letter-spacing: 0.4px;
    }

    .card_button {
        border-radius: 0.125rem;
        display: block;
        height: 30px;
        width: 100%;
        font-size: 13px;
        text-decoration: none;
        margin: auto 0 0;
        color: $white;
        background-color: #517398;
        font-family: Roboto, sans-serif;
        font-weight: 500;
        letter-spacing: 0.5px;
        text-align: center;
        overflow: hidden;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
        border: 1px solid $white;
    }

    .button_container {
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .show-more_button {
        width: 31rem;
        height: 2.5rem;
        border-radius: 0.25rem;
        box-shadow: 0 2px 4px 0 rgba(81, 115, 152, 0.2);
        background-color: $white;
        color: $black;
        font-family: Roboto, sans-serif;
        text-decoration: none;
        font-size: 0.875rem;
        font-weight: 500;
        letter-spacing: 0.5px;
        text-align: center;
        overflow: hidden;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>

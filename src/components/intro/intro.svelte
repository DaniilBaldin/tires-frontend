<script>
    import { onMount } from 'svelte';
    import axios from 'axios';

    const endpoint = import.meta.env.PUBLIC_BASE_URL;

    let makers = [];
    let models = [];
    let years = [];
    let searchResults = [];

    let maker = '';
    let model = '';
    let year = '';
    let searchResult = '';

    onMount(async function () {
        searchResult = '';
        const response = await axios.get(`${endpoint}rims/makers`);
        const data = response.data;
        makers = data;
    });

    async function selectMaker(mkr) {
        maker = mkr;
        const response = await axios.get(`${endpoint}rims/models?mark=${maker.replace(' ', '')}`);
        const data = response.data;
        models = data;
    }

    async function selectModel(mdl) {
        model = mdl;
        const modelSelected = models.filter((model) => model.model === mdl);
        const response = await axios.get(`${endpoint}rims/years?modelId=${modelSelected[0].modelId}`);
        const data = response.data;
        years.push(Object.keys(data));
        years = years[0];
    }

    async function onSubmit() {
        window.location.replace(`${window.location}disks?maker=${maker}&model=${model}&year=${year}`);
    }

    function onFocus() {
        document.getElementById('blur').style.display = 'block';
    }

    function onFocusOut() {
        document.getElementById('blur').style.display = 'none';
        searchResult = '';
        onSearch(searchResult);
    }

    async function onSearch(searchValue) {
        searchResult = searchValue;
        const response = await axios.get(`${endpoint}rims/search?substring=${searchValue}`);
        const data = response.data;
        if (searchResult) {
            searchResults = data.slice(0, 10);
        } else {
            searchResults = [];
        }
    }
</script>

<section>
    <div
        class="container"
        style="position:relative, z-index:3"
    >
        <div
            id="blur"
            class="blury"
        />
        <form class="input-form">
            <img
                class="search-logo"
                src="/Search.svg"
                alt="Search"
                width="20px"
                height="20px"
            />
            <input
                class="inner-input"
                type="text"
                placeholder="Поиск по дискам"
                value={searchResult}
                on:focus={onFocus}
                on:blur={onFocusOut}
                on:input|preventDefault={(event) => {
                    if (event.target.value < 1) searchResult = [];
                    onSearch(event.target.value);
                }}
            />
        </form>
        {#if searchResults.length}
            <div
                class="search_results"
                id="result"
            >
                {#each searchResults as result}
                    <a
                        class="search_result-link"
                        href={`/disk/${result.id}`}
                    >
                        <img
                            class="search_result-span"
                            src={`${endpoint}images/${result.thumbnail}`}
                            alt="Span"
                        />
                        <div class="search_result-container">
                            <p class="search_result-name">{result.name}</p>
                            <p class="search_result-price">от {(result.minPrice * 36.6).toFixed(0)} грн.</p>
                        </div></a
                    >
                {/each}
            </div>
        {:else}
            <div />
        {/if}
        <div class="selector-container">
            <div class="image-container">
                <img
                    src="/Cars.png"
                    alt="Cars"
                    width="165"
                    height="165"
                />
            </div>
            <form
                id="selectForm"
                class="selectors-wrapper"
                on:submit|preventDefault={onSubmit}
            >
                <legend
                    for="selectForm"
                    class="label">Подбор по авто</legend
                >
                <div class="selector-wrapper">
                    <select
                        class="selector"
                        name="makers"
                        id="makerSelect"
                        on:change={(event) => {
                            selectMaker(event.target.value);
                        }}
                    >
                        <option value="">Марка</option>
                        {#each makers as maker}
                            <option value={maker.maker}>{maker.maker}</option>
                        {/each}
                    </select>
                </div>
                <div class="selector-wrapper">
                    <select
                        class="selector"
                        name="models"
                        id="modelSelect"
                        on:change={(event) => {
                            selectModel(event.target.value);
                        }}
                    >
                        <option value="">Модель</option>
                        {#if models.length}
                            {#each models as model}
                                <option value={model.model}>{model.model}</option>
                            {/each}
                        {/if}
                    </select>
                </div>
                <div class="selector-wrapper">
                    <select
                        class="selector"
                        name="years"
                        id="yearSelect"
                        on:change={(event) => {
                            year = event.target.value;
                        }}
                    >
                        <option value="">Год</option>
                        {#if years.length}
                            {#each years as y}
                                <option value={y}>{y}</option>
                            {/each}
                        {/if}
                    </select>
                </div>

                <button
                    disabled={!maker || !model || !year}
                    class="form-button">Подобрать</button
                >
            </form>
        </div>
    </div>
    <div id="overlay" />
</section>

<style lang="scss">
    @import '../../styles/variables.scss';

    section {
        height: 21rem;
        width: 100%;
        background: linear-gradient(0deg, #507299, #2d435c);
        display: flex;
        align-items: center;
        justify-content: center;
        /* position: relative; */
    }

    .container {
        top: 5.5rem;
        width: 488px;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
        position: relative;
    }

    .input-form {
        width: 362px;
        height: 3rem;
        border: 1px solid white;
        margin: 0;
        padding: 10px 8px 8px 48px;
        background: $white;
        position: relative;
        border-radius: 4px;
        margin-bottom: 8px;
        z-index: 5;
        opacity: 1;
        /* position: relative; */
    }

    .blury {
        position: fixed;
        height: 100%;
        width: 100%;
        background-color: black;
        top: 0;
        left: 0;
        box-sizing: border-box;
        opacity: 0.5;
        display: none;
        z-index: 4;
    }

    .inner-input {
        background: transparent;
        border: 1px solid white;
        line-height: 1.2rem;
        min-height: 1.2rem;
        font-size: 1rem;
        outline: none;
        width: 100%;
        height: 100%;
        vertical-align: middle;
        z-index: 5;
        /* padding: 1px 2px 1px 2px; */

        &::placeholder {
            opacity: 0.8;
            font-size: 1rem;
            letter-spacing: 0.6px;
        }
    }

    .search-logo {
        position: absolute;
        left: 14px;
        top: 14px;
        z-index: 5;
    }

    .selector-container {
        width: 100%;
        height: 15.75rem;
        background: $white;
        border: none;
        border-radius: 4px;
        padding: 1.5rem 2rem 1.5rem 2.5rem;
        display: flex;
        box-shadow: 0 0 4px 0 rgba(0, 0, 0, 0.2);
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 40px;
        z-index: 0;

        @media (max-width: 500px) {
            padding: 1.5rem 2rem 1.5rem 1.5rem;
        }
    }

    .image-container {
        border: 1px solid $white;
        width: 165px;
        height: 165px;
        border-radius: 50%;
        object-fit: contain;

        @media (max-width: 500px) {
            display: none;
        }
    }

    .selectors-wrapper {
        width: 100%;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        /* padding-top: 5px; */
    }

    .selector-wrapper {
        background-color: $selector-main;
        width: 100%;
        height: 30px;
        position: relative;
        border-radius: 3px;
        cursor: pointer;
        margin-bottom: 10px;

        &::before {
            position: absolute;
            display: block;
            content: '';
            cursor: pointer;
            right: 8px;
            top: 14px;
            width: 0;
            height: 0;
            border-left: 5px solid transparent;
            border-right: 5px solid transparent;
            border-top: 5px solid $selector-secondary;
        }
    }

    .selector {
        width: 100%;
        height: 100%;
        display: block;
        position: relative;
        cursor: pointer;
        outline: none;
        padding-left: 0.5rem !important;
        padding-right: 0.5rem !important;
        text-overflow: ellipsis;
        white-space: nowrap;
        font-size: 0.85rem;
        color: $selector-secondary;
        background-color: transparent;
        background-repeat: no-repeat;
        border: none;
        border-radius: 2px;
        -webkit-border-radius: 2px;
        -webkit-padding-start: 0;
        -webkit-padding-end: 0;
        user-select: none;
        -webkit-user-select: none;
        appearance: none;
        -webkit-appearance: none;
    }

    .label {
        font-size: 1.125rem;
        font-weight: 600;
        color: rgba(66, 95, 128, 0.78);
        letter-spacing: 0.6px;
        align-self: center;
        margin-bottom: 10px;
        text-align: center;
    }

    .form-button {
        width: 100%;
        height: 2.25rem;
        border-radius: 0.125rem;
        display: block;
        height: 2.25rem;
        font-family: Roboto, sans-serif;
        font-size: 0.875rem;
        font-weight: 500;
        background-color: #517398;
        color: $white;
        text-align: center;
        overflow: hidden;
        cursor: pointer;
        border: 1px solid #517398;
        outline: none;
        margin-top: 1.2rem;

        &:disabled {
            cursor: auto;
        }
    }

    .search_results {
        margin: 8px 0;
        position: absolute;
        top: 14%;
        left: 13%;
        border-radius: 3px;
        overflow: hidden;
        width: 362px;
        background-color: $white;
        padding: 4px 0;
        z-index: 4;
        display: block;
    }

    .search_result-link {
        display: block;
        width: 100%;
        padding: 4px 8px;
        box-sizing: border-box;
        height: 44px;
        background-color: $white;
        cursor: pointer;
        transition: background-color 0.1s ease-in-out;
        z-index: 5;
        text-decoration: none;

        &:hover {
            background-color: antiquewhite;
        }
    }

    .search_result-span {
        display: block;
        float: left;
        border-radius: 2px;
        height: 36px;
        width: 36px;
        background-position: 50%;
        background-size: contain;
        background-repeat: no-repeat;
    }

    .search_result-container {
        display: flex;
        flex-direction: column;
        align-items: left;
        justify-content: flex-start;
        margin-left: 50px;
        gap: 5px;
        padding-top: 3px;
    }

    .search_result-name {
        margin: 0;
        text-decoration: none;
        font-size: 14px;
        /* height: 50%; */
        width: 100%;
        line-height: 100%;
        color: #507299;
    }
    .search_result-price {
        margin: 0;
        display: block;
        width: 100%;
        line-height: 100%;
        /* height: 50%; */
        font-size: 12px;
        color: #939393;
    }
</style>

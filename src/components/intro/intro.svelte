<script>
    import { makers } from "src/ts/makers";
</script>


<section>
    <div class="container">
        <div class="inner-container">
            <form class="input-form">
                <img class="search-logo" src="/Search.svg" alt="Search">
                <input class="inner-input" type="text" placeholder="Поиск по дискам">
            </form>
            <div class="selector-container">
                <div class="image-container">
                    <img src="/Cars.png" alt="Cars" width="165" height="165" >
                </div>
                <form id="selectForm" class="selectors-wrapper">
                    <legend for="selectForm" class="label">Подбор по авто</legend>
                    <div class="selector-wrapper">
                        <select class="selector" name="makers" id="">
                        <option value="">Марка</option>
                        {#each makers as maker }
                        <option value={maker.maker}>{maker.maker}</option>                            
                        {/each}
                    </select>
                    </div>
                    <div class="selector-wrapper">
                        <select class="selector" name="models" id="">
                        <option value="">Модель</option>
                        <!-- {#each makers as maker }
                        <option value={maker.maker}>{maker.maker}</option>                            
                        {/each} -->
                    </select>
                    </div>
                    <div class="selector-wrapper">
                        <select class="selector" name="years" id="">
                        <option value="">Год</option>
                        <!-- {#each makers as maker }
                        <option value={maker.maker}>{maker.maker}</option>                            
                        {/each} -->
                    </select>
                    </div>
                    
                    <button class="form-button">Подобрать</button>
                </form>
            </div>
        </div>
    </div>
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
    }

    .container {
        width: 100%;
        max-width: 64rem;
        height: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-end;
        position: relative;
    }

    .inner-container {
        position: absolute;
        bottom: 0;
        left: 0%;
        transform: translate(52%, 20%),;
        width: 500px;
        height: 300px;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;

        @media (max-width: 950px) {
            transform: translate(35%, 20%);
        };

        @media (max-width: 850px) {
            transform: translate(25%, 20%);
        };

        @media (max-width: 720px) {
            width: 100%;
            transform: translate(0, 20%);
        }
    }

    .input-form {
        width: 80%;
        height: 3rem;
        border: 1px solid white;
        margin: 0;
        padding: 10px 8px 8px 48px;
        background: $white;
        position: relative;
        border-radius: 4px;
        margin-bottom: 10px;
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
    }

    .selector-container {
        width: 100%;
        height: 15.75rem;
        background: $white;
        border: none;
        border-radius: 4px;
        padding: 1.5rem 2rem 1.5rem 2.5rem;
        display: flex;
        box-shadow: 0 0 4px 0 rgba(0,0,0,0.2);
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap:50px;

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
    }

    .selector-wrapper {
        background-color: $selector-main;
        width:100%;
        height: 30px;
        position: relative;
        border-radius: 3px;
        cursor: pointer;
        margin-bottom: 10px;

        &::before {
           position: absolute; 
           display: block;
           content: "";
           cursor: pointer;
           right: 8px;
           top:14px;
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
        font-size: .85rem;
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
        font-weight: 500;
        color: rgba(66,95, 128, .78);
        letter-spacing: .6px;
        align-self: center;
        margin-bottom: 5px;
    }

    .form-button {
        width: 100%;
        height: 2.25rem;
        border-radius: 0.125rem;
        display: block;
        height: 2.25rem;
        font-family: Roboto, sans-serif;
        font-size: .875rem;
        font-weight: 500;
        background-color:#435f80;
        color:$white;
        text-align: center;
        overflow: hidden;
        cursor: pointer;
        border: none;
        outline: none;
        margin-top: 2rem;
    }

    
</style>
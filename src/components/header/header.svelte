<script>
    import Contacts from '~components/modal/contacts/contacts.svelte';
    let showModal = false;
</script>

<header class="header_page">
    <div class="container">
        <a
            href="/"
            class="logo"
        >
            <img
                src="/TireLogo.png"
                alt="Logo"
                width={35}
                height={35}
            />Ukrdisk</a
        >
        <div class="button-container">
            <a
                class="button_link"
                href="https://mmr.net.ua/cat/autoworld">Новости</a
            >
            <!-- svelte-ignore a11y-missing-attribute -->
            <a
                class="button_link"
                aria-hidden="true"
                on:click={() => (showModal = true)}>Контакты</a
            >
            <Contacts bind:showModal />
        </div>
    </div>
</header>

<style lang="scss">
    @import '../../styles/variables.scss';

    header {
        display: block;
    }

    .header_page {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        padding: 0.5rem;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .container {
        position: relative;
        padding: 0;
        margin: 0;
        width: 100%;
        max-width: 64rem;
        display: flex;
        align-items: center;
        justify-content: space-between;
        padding: 0px 1rem;
    }

    .logo {
        display: flex;
        display: -webkit-flex;
        align-items: center;
        -webkit-align-items: center;
        justify-content: space-between;
        -webkit-justify-content: space-between;
        padding: 0;
        margin: 0;
        gap: 10px;
        font-family: Rubik, sans-serif;
        font-size: 1.5rem;
        font-weight: 500;
        text-decoration: none;
        color: $white;
        letter-spacing: 0.9px;
        cursor: pointer;
        position: relative;
    }

    .button-container {
        display: flex;
        gap: 5px;
    }

    .button_link {
        width: 80px;
        height: 30px;
        padding: 0;
        background-color: transparent;
        border: none;
        outline: none;
        color: $white;
        text-decoration: none;
        display: flex;
        align-items: center;
        justify-content: center;
        cursor: pointer;
        font-family: Roboto, sans-serif;
        font-size: 1rem;
        font-weight: 550;
        letter-spacing: 0.5px;

        &:hover {
            text-decoration: underline;
        }
    }
</style>

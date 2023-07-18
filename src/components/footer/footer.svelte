<script>
    import Contacts from '~components/modal/contacts/contacts.svelte';
    let showModal = false;
</script>

<footer>
    <div class="container">
        <div class="logo_container">
            <a
                class="logo_link"
                href="/"
            >
                <img
                    class="logo"
                    src="/TireLogo.png"
                    alt="Logo"
                />UkrDisk
            </a>
        </div>
        <div class="links_container">
            <a
                class="link"
                href="disks/inziaone"
            >
                Диски InziAone
            </a>
            <a
                class="link"
                href="disks/kosei"
            >
                Диски Kosei
            </a>
            <a
                class="link"
                href="disks/marcello"
            >
                Диски Marcello
            </a>
            <a
                class="link"
                href="disks/mkw"
            >
                Диски MKW
            </a>
            <a
                class="link"
                href="disks/replica"
            >
                Диски Replica
            </a>
            <a
                class="link"
                href="disks"
            >
                Подбор дисков по авто
            </a>
            <a
                class="link"
                href="https://mmr.net.ua/cat/autoworld"
            >
                Новости мира авто
            </a>
            <a
                class="link"
                href="/"
            >
                О нас
            </a>
        </div>
        <div class="contacts_container">
            <a
                class="icon_button"
                href="mailto:blokhvova@gmail.com"
                target="_blank"
                rel="noreferrer noppener"
            >
                <img
                    class="icon"
                    src="/mailIcon.png"
                    alt="Mail"
                />
            </a>
            <button
                class="icon_button"
                on:click={() => (showModal = true)}
            >
                <img
                    class="icon"
                    src="/contactsIcon.jpeg"
                    alt="Contacts"
                />
            </button>
            <Contacts bind:showModal />
        </div>
    </div>
</footer>

<style lang="scss">
    @import '../../styles/variables.scss';

    footer {
        width: 100%;
        margin-top: 1rem;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .container {
        width: 100%;
        max-width: 64rem;
        height: 100px;
        min-height: 72px;
        border-top: 1px solid #e4e8ed;
        margin: 0 auto;
        padding: 0;
        display: flex;
        flex-direction: row;
        align-items: top;
        justify-content: flex-start;
        padding-top: 10px;
        margin-bottom: 30px;
    }
    .logo_container {
        width: 30%;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .logo_link {
        display: flex;
        display: -webkit-flex;
        align-items: center;
        -webkit-align-items: center;
        justify-content: flex-start;
        -webkit-justify-content: flex-start;
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
    }

    .logo {
        width: 50px;
        height: 50px;
        object-fit: contain;
        overflow: hidden;
    }

    .links_container {
        display: flex;
        flex-wrap: wrap;
        flex-direction: column;
        align-items: left;
        justify-content: flex-start;
        max-height: 100px;
        width: 40%;
        padding: 0;
    }

    .link {
        text-decoration: none;
        color: grey;
    }

    .contacts_container {
        width: 30%;
        padding: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 20px;
    }

    .icon {
        width: 50px;
        height: 50px;
        border-radius: 50%;
        border: none;
        outline: none;
    }

    .icon_button {
        width: 50px;
        height: 50px;
        border-radius: 50%;
        border: none;
        outline: none;
        background-color: transparent;
        object-fit: contain;
        padding: 0;
    }
</style>

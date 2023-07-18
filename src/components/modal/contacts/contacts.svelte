<script>
    export let dialog;
    export let showModal;

    $: if (dialog && showModal) dialog.showModal();
</script>

{#if showModal}
    <dialog
        bind:this={dialog}
        on:close={() => (showModal = false)}
    >
        <div class="container">
            <div class="header">
                <p class="header_title">Наши контакты</p>
            </div>
            <div
                class="contacts"
                style="align-items:self-end"
            >
                <span class="contact_title">Наш e-mail:</span>
                <a
                    class="mail"
                    href="mailto:blokhvova@gmail.com"
                    target="_blank"
                    rel="noreferrer noppener">blokhvova@gmail.com</a
                >
            </div>
            <div
                class="contacts"
                style="align-items:center"
            >
                <span class="contact_title">Наш телефон:</span>
                <p class="mail">(050) 340-37-26</p>
            </div>
            <div class="button_container">
                <button
                    class="close_button"
                    on:click={() => (showModal = false)}>Закрыть</button
                >
            </div>
        </div>
    </dialog>
{/if}

<style>
    dialog {
        width: 350px;
        height: 250px;
        border: none;
        outline: none;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
        border-radius: 0.2em;
        padding: 0;
    }

    dialog::backdrop {
        background: rgba(0, 0, 0, 0.3);
    }

    dialog[open] {
        animation: zoom 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
    }
    @keyframes zoom {
        from {
            transform: scale(0.95);
        }
        to {
            transform: scale(1);
        }
    }
    dialog[open]::backdrop {
        animation: fade 0.2s ease-out;
    }
    @keyframes fade {
        from {
            opacity: 0;
        }
        to {
            opacity: 1;
        }
    }

    .container {
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .header {
        height: 30%;
        width: 100%;
        border: none;
        padding: 24px 20px;
        background-color: #eceff1;
        border-bottom: 1px solid #c4c8cc;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .contacts {
        height: 20%;
        width: 85%;
        display: flex;
        justify-content: space-between;
    }

    .button_container {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
        height: 30%;
        padding: 20px 24px;
    }

    .header_title {
        margin: 0;
        margin-top: 3px;
        text-transform: uppercase;
        color: #7a8999;
        font-size: 16px;
        text-align: center;
        letter-spacing: 0.5px;
    }

    .close_button {
        height: 36px;
        width: 100%;
        border: 1px solid #507299;
        background-color: #507299;
        outline: none;
        border-radius: 2px;
        color: white;
    }

    .contact_title {
        color: rgba(0, 0, 0, 0.8);
        font-size: 16px;
        margin: 0;
        line-height: 20px;
    }

    .mail {
        text-decoration: none;
        color: rgba(0, 0, 0, 0.8);
        font-size: 16px;
        margin: 0;
        line-height: 20px;

        &:hover {
            text-decoration: underline;
            cursor: pointer;
        }
    }
</style>

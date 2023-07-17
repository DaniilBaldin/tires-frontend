<header>
    <div class="container">
        <a href="/" class="logo">
        <img src="/TireLogo.png" alt="Logo" width={30} height={30}>Ukrdisk</a>
        <div class="button-container">
            <button class="button">Новости</button>
            <button class="button">Контакты</button>
        </div>
    </div>
</header>

<style lang="scss">
    @import '../../styles/variables.scss'; 

    header{
        width:100%;
        /* max-width: 60vw; */
        background-color: transparent;
        border: none;
        padding: 0px 0 10px 0;
        /* min-height: 80px; */
        position: relative !important;
        background-color: #2d435c;
        top:0;
        left: 0;
        display: flex;
        align-items: center;
        justify-content: center;
        z-index: 1000;

        @media (max-width:1100px) {
            padding-left: 20px;
            padding-right: 30px;
        }
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
        padding-top: 10px;
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
    }

    .button-container {
        display: flex;
        gap: 5px;
    }

    .button {
        width: 80px;
        height: 30px;
        background-color: transparent;
        border: none;
        outline: none;
        color:$white;
    }
</style>
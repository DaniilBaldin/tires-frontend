<section>
    <div class="container">
        <div class="content">
            <a href="/disks/replica" class="card">
            <img class="car-image" src="/Car.png" alt="Car">
        <div class="side-wrap">
            <h2 class="title">Replica</h2>
            <p class="subtitle">Копии оригинальных дисков теперь у нас на сайте</p>
            <button class="button">Посмотреть все</button>
        </div></a>
        </div>
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
        margin-bottom: 20px;
    }

    .container {
        width: 100%;
        max-width: 64rem;
        margin: 0 auto;
    }

    .content{
        width: 100%;
        padding: 0;
        margin: 0 auto;
    }

    .card {
        display: flex;
        flex-direction: row;
        align-items: stretch;
        border-radius: 0.25rem;
        box-shadow: 0 2px 4px 0 rgba(81, 115, 112, .2);
        overflow: hidden;
        background-color: $white;
        padding: 2.25rem 2rem 0.75rem;
        width:100%;
        flex-wrap: wrap;
        text-decoration: none;
    }

    .car-image {
       height: 200px; 
       width: 50%;
       order:1;
    }

    .side-wrap {
        width: 50%;
        padding: 0;
        order:2;
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;
    }

    .title {
        display: block;
        color:black;
        font-size: 32px;
        font-weight: 800;
        letter-spacing: 1.2px;
        margin: 0;
        margin-bottom: 16px;
        
    }

    .subtitle {
        color: rgb(0, 0, 0);
        width: 80%;
        font-size: 20px;
        font-weight: 400;
        letter-spacing: 1.2px;
        display: block;
        margin-block-start: 0.83em;
        margin-block-end: 0.83em;
        text-align: center;
        margin: 0 auto;
    }

    .button {
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
        margin: 30px auto;
        
        &:hover {
            background-color: #ebf0f5;
        }
    }
</style>
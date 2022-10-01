<script>
    let saboo = "";
    let getBress = "ร่วมบูชา พระคณิตกรณ์";
    let isFinish = true;

    import { BlessList } from "./Data/Bless";
    addEventListener("keyup", function (e) {
        e.preventDefault();
        if (e.key == "f" && isFinish) {
            /* Do whatever */
            worship();
        }
    });

    const worship = () => {
        if (isFinish) {
            isFinish = false;
            saboo = "holy";
            setTimeout(() => {
                getBress =
                    BlessList[Math.floor(Math.random() * BlessList.length)];
            }, 15000);
            setTimeout(() => {
                saboo = "";
                isFinish = true;
            }, 30000);
        }
    };
</script>

<svelte:window />

<main>
    <h1 id="holy" class={saboo}>{getBress}</h1>
    <h2 class={isFinish ? "click" : "click go"} on:click={worship}>
        กด f หรือคลิกเพื่อบูชา
    </h2>
    <div>
        <a target="_blank" href="https://github.com/Hakata111/holy-thing">
            <img class="github-icon" src="/github.png" alt="github icon" />
        </a>
    </div>
</main>

<style>
    .github-icon {
        margin: 10px;
        width: 50px;
        position: fixed;
        bottom: 0;
        right: 0;
    }
    .click {
        cursor: pointer;
    }
    .click:hover {
        text-decoration: underline;
    }
    #holy {
        display: inline-block;
    }
    .go {
        opacity: 0;
        animation: gone 7s ease;
    }
    @keyframes gone {
        0% {
            opacity: 1;
            transform: translate(0, 0);
        }
        50% {
            opacity: 0.5;
        }
        100% {
            opacity: 0;
            transform: translate(0, -100px);
        }
    }
</style>

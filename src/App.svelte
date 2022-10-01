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
    <h2 style="{isFinish ?"opacity: 1;" : "opacity: 0;"}">กด f เพื่อบูชา</h2>
</main>

<style>
  .opacity-0 {
    opacity: 0;
  }
</style>

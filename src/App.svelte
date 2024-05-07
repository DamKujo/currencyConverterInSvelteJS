<script>
  import Converter from './lib/Converter.svelte'
  import sberImg from './assets/sber.svg'
  import dollarImg from './assets/dollar.svg'
  import euroImg from './assets/euro.svg'
  import rubImg from './assets/rub.svg'
</script>

<main>
  <div>
    <a href="https://www.sberbank.ru/ru/person" target="_blank" rel="noreferrer">
      <img src={dollarImg} class="logo" alt="Vite Logo" />
    </a>
    <a href="https://www.vtb.ru/" target="_blank" rel="noreferrer">
      <img src={rubImg} class="logo rub" alt="Svelte Logo" />
    </a>
    <a href="https://www.tinkoff.ru/" target="_blank" rel="noreferrer">
      <img src={euroImg} class="logo euro" alt="Svelte Logo" />
    </a>
  </div>
  <div class="block">
    <h1>Currency converter</h1>
  </div>
  

  <div class="card">
    <Converter />
  </div>
</main>

<style>
  .logo {
    height: 6em;
    padding: 2.5em;
    will-change: filter;
    transition: filter 300ms;
  }
  .logo:hover {
    filter: drop-shadow(0 0 3em #2cff5aaa);
  }
  .logo.rub:hover {
    filter: drop-shadow(0 0 2em #00a2ffaa);
  }
  .logo.euro:hover{
    filter: drop-shadow(0 0 2em #ff4800aa);
  }
  .block{
    display: flex;
    padding: 1.5em;
    justify-content: center;
  }
  .sber{
    height: 6em;
    padding: 1.5em;
    will-change: filter;
    transition: filter 300ms;
    padding-right: 30px;
  }
  .sber:hover{
    filter: drop-shadow(0 0 4em #009b22aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>

<script lang="ts">
  import 'tw-elements';

  import { DateInput } from 'date-picker-svelte';
  let date = new Date();

  let user = window.Telegram.WebApp.initDataUnsafe.user.first_name + "\n" +
             window.Telegram.WebApp.initDataUnsafe.user.last_name+ "("+window.Telegram.WebApp.initDataUnsafe.user.username+")"

  window.Telegram.WebApp.MainButton.text = "ЗАКpppppppЗАТЬ СЪЁМКУ";
  window.Telegram.WebApp.MainButton.isVisible = true;
  window.Telegram.WebApp.MainButton.color = "#212121";
  window.Telegram.WebApp.MainButton.onClick(() => {
    window.Telegram.WebApp.MainButton.text = "ОТМЕНИТЬ СТАНЦИЮ"
    window.Telegram.WebApp.showAlert({message:"Ghbdtn!", title: "dfdfgdfg"})
  })

  window.Telegram.WebApp.BackButton.isVisible = true;

  

</script>



  <div class="header">
    <button> Обо мне </button>
    <button> Портфолио </button>
    <button> Записаться </button>
  </div>

  <DateInput bind:value={date} />

  {user}

  <div id="carouselExampleControls" class="carousel slide relative" data-bs-ride="carousel">
    <div class="carousel-inner relative w-full overflow-hidden">
      <div class="carousel-item active relative float-left w-full">
        <img 
          src="ph2.png"
          class="block w-full"
          alt="Wild Landscape"
        />
      </div>
      <div class="carousel-item relative float-left w-full">
        <img
          src="ph3.png"
          class="block w-full"
          alt="Camera"
        />
      </div>
      <div class="carousel-item relative float-left w-full">
        <img
          src="ph1.png"
          class="block w-full"
          alt="Exotic Fruits"
        />
      </div>
    </div>
    <button
      class="carousel-control-prev absolute top-0 bottom-0 flex items-center justify-center p-0 text-center border-0 hover:outline-none hover:no-underline focus:outline-none focus:no-underline left-0"
      type="button"
      data-bs-target="#carouselExampleControls"
      data-bs-slide="prev"
    >
      <span class="carousel-control-prev-icon inline-block bg-no-repeat" aria-hidden="true"></span>
      <span class="visually-hidden">Previous</span>
    </button>
    <button
      class="carousel-control-next absolute top-0 bottom-0 flex items-center justify-center p-0 text-center border-0 hover:outline-none hover:no-underline focus:outline-none focus:no-underline right-0"
      type="button"
      data-bs-target="#carouselExampleControls"
      data-bs-slide="next"
    >
      <span class="carousel-control-next-icon inline-block bg-no-repeat" aria-hidden="true"></span>
      <span class="visually-hidden">Next</span>
    </button>
  </div>

<style>
  .header{
    position: absolute;
    top: 0px;
    left: 0px;
    width: 100%;
  }
  .logo {
    height: 6em;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
  .read-the-docs {
    color: #888;
  }
</style>
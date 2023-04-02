<script lang="ts">
  import { onMount } from 'svelte';
  import svelteLogo from './assets/svelte.svg'
  
  let assignments = []
  let dueToday = []
  let dueTomorrow = []
  let dueLater = []

  const credentials = {
    user: 'adomaitisc',
    passwd: 'No password for you',
  }

  const requestUrl = 'https://webwork.wit.edu/webwork2/MATH2860-Spring2023-Minevich/';

  // send request and scrape the html
  onMount(async function () {
    const res = await fetch(requestUrl, {
      method: 'POST',
      headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
      },
      body: new URLSearchParams(credentials),
    })
    console.log(res)
  });
</script>

<main class="bg-stone-200 w-screen h-screen flex items-center justify-center overflow-hidden">
  <div class="bg-stone-100 p-8 h-1/2 w-1/2 rounded-2xl shadow-sm flex flex-col items-start justify-start">
    <div class="flex justify-between w-full">
      <!-- logo + name -->
      <div class="flex items-end gap-1.5">
          <img src={svelteLogo} alt="Svelte logo" class="h-6" />
        <h1 class=" text-stone-800 leading-none text-xl">Webwork</h1>
      </div>
      <!-- settings -->
      <div class="flex items-end">
        <p class="text-stone-800 text-sm leading-none">Account</p>
      </div>
  </div>
  <div class="w-full h-[1px] bg-stone-200 my-3"/>
  <div class="flex flex-col gap-3 overflow-auto">
    <div class="text-sm text-stone-400">
      <h2>Due today</h2>
    </div>
    <div class="text-sm text-stone-400">
      <h3>Due tomorrow</h3>
    </div>
    <div class="text-sm text-stone-400">
      <h3>Due later</h3>
    </div>
  </div>
</main>

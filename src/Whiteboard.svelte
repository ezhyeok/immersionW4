<script>
  import { Link } from 'svelte-routing';
  import { fade } from 'svelte/transition';
  import { onMount } from 'svelte';

  let currentText = 0;
  const texts = ["똑똑하게", "효율적으로", "자신있게"];

  onMount(() => {
    setInterval(() => {
      currentText = (currentText + 1) % texts.length;
    }, 2000); // Change text every 2 seconds
  });
</script>

<style>
  .container {
    font-family: 'CustomFont', Arial, sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    background-color: white;
  }

  .header {
    width: 100%;
    background-color: black;
    color: white;
    padding: 15px 10px; /* Increase padding for height */
    text-align: center;
    font-size: 24px;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
    line-height: 1.5; /* Increase line-height */
  }

  .header-content {
    display: flex;
    justify-content: space-between;
    max-width: 1200px;
    margin: 0 auto;
    width: 100%;
  }

  .header a {
    color: white;
    text-decoration: none;
    margin: 0 20px;
  }

  .header a:hover {
    text-decoration: underline;
  }

  .title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 20px;
    margin-top: 90px; /* Adjust top margin to avoid overlap with fixed header */
  }

  .text {
    font-size: 90px;
    text-align: center;
    width: 50%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    line-height: 1.7;
    margin-left: -50px;
  }

  .image-container {
    width: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .image {
    width: auto;
    height: 700px;
  }

  .text-transition {
    position: relative;
    display: inline-block;
  }

  .text-transition span {
    position: absolute;
    white-space: nowrap;
    transition: opacity 1s ease-in-out;
  }

  .text-transition span:not(.current) {
    opacity: 0;
  }

  .text-transition span.current {
    opacity: 1;
  }
</style>

<div class="container">
  <div class="header">
    <div class="header-content">
      <span>WHITEBOARD</span>
      <div>
        <Link to="/">HOME</Link>
        <Link to="/ppt">PPT</Link>
        <Link to="/video">영상</Link>
        <Link to="/mypage">mypage</Link>
      </div>
    </div>
  </div>
  <div class="title">
    <div class="text">
      <div>발표를 더</div>
      <div class="text-transition">
        {#each texts as text, i}
          <span class={currentText === i ? 'current' : ''}>{text}</span>
        {/each}
      </div>
    </div>
    <div class="image-container">
      <img class="image" src="nubduck.png" alt="nubduck" />
    </div>
  </div>
</div>

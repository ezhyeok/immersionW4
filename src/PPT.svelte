<script>
  import { Link } from 'svelte-routing';
  import { writable } from 'svelte/store';

  let presentationTopic = '';
  let relatedContent = '';
  let pptCount = '';
  let presentationTime = '';
  let showCompletionMessage = writable(false);
  let selectedTemplate = writable(null);

  function handleSubmit() {
    showCompletionMessage.set(true);
  }

  function handleTemplateSelection(template) {
    selectedTemplate.set(template);
  }
</script>

<style>
  @import './common.css';

  .container {
    font-family: 'CustomFont', Arial, sans-serif;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
    min-height: 100vh;
    background-color: white;
  }

  .header {
    width: 100%;
    background-color: black;
    color: white;
    padding: 15px 10px;
    text-align: center;
    font-size: 24px;
    position: fixed;
    top: 0;
    left: 0;
    z-index: 1000;
    line-height: 1.5;
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

  .content {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    padding: 20px;
    margin-top: 90px; /* Adjust top margin to avoid overlap with fixed header */
  }

  .form-container {
    background-color: #fff4cc;
    padding: 20px;
    border-radius: 10px;
    width: 80%;
    max-width: 1000px; /* Adjust as needed */
    text-align: center;
    margin-bottom: 20px;
  }

  .form-container label {
    display: block;
    margin: 10px 0 5px;
    font-weight: bold;
  }

  .form-container input {
    width: calc(100% - 20px);
    padding: 10px;
    margin-bottom: 10px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: white;
    box-shadow: inset 0 1px 3px rgba(0, 0, 0, 0.1);
    margin-left: 10px;
  }

  .image-container {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
    justify-items: center;
    align-items: center;
  }

  .image-container img {
    width: 100%;
    max-width: 300px;
    cursor: pointer;
    border: 2px solid transparent;
    border-radius: 10px;
    transition: transform 0.3s, border-color 0.3s;
  }

  .image-container img:hover, .image-container img.selected {
    transform: scale(1.05);
    border-color: #ff6347; /* Change color as needed */
  }

  .submit-button {
    width: 100px;
    padding: 10px;
    background-color: #FF6347; /* Change color as needed */
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin: 20px auto 0; /* Center the button horizontally */
    display: block; /* Make the button a block-level element */
  }

  .title {
    font-size: 24px;
    margin-bottom: 20px;
  }

  .completion-message {
    font-size: 24px;
    margin-top: 50px;
    text-align: center;
  }

  .completion-images {
    display: flex;
    justify-content: space-around;
    margin-top: 20px;
    width: 100%;
  }

  .completion-images img {
    width: 45%;
    max-width: 600px;
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
  
  <div class="content">
    {#if $showCompletionMessage}
      <div>
        <div class="completion-message">PPT와 대본 생성이 완료됐습니다!</div>
        <div class="completion-images">
          <img src="jib1.png" alt="PPT Image">
          <img src="jib2.png" alt="Script Image">
        </div>
      </div>
    {:else}
      <div class="form-container">
        <h2 class="form-title">발표에 대해 알려주세요!</h2>
        <div class="form-row">
          <label for="topic">발표의 주제?</label>
          <input type="text" id="topic" bind:value={presentationTopic} placeholder="발표 주제를 입력하세요">
        </div>
        <div class="form-row">
          <label for="content">관련 내용?</label>
          <input type="text" id="content" bind:value={relatedContent} placeholder="관련 내용을 입력하세요">
        </div>
        <div class="form-row">
          <label for="pptCount">PPT 장수?</label>
          <input type="text" id="pptCount" bind:value={pptCount} placeholder="PPT 장수를 입력하세요">
        </div>
        <div class="form-row">
          <label for="time">발표 시간?</label>
          <input type="text" id="time" bind:value={presentationTime} placeholder="발표 시간을 입력하세요">
        </div>

        <div class="title">PPT 템플릿을 골라주세요!</div>
        <div class="image-container">
          <img src="ppt1.png" alt="Template 1" class:selected={$selectedTemplate === 'template1'} on:click={() => handleTemplateSelection('template1')}/>
          <img src="ppt2.png" alt="Template 2" class:selected={$selectedTemplate === 'template2'} on:click={() => handleTemplateSelection('template2')}/>
          <img src="ppt3.png" alt="Template 3" class:selected={$selectedTemplate === 'template3'} on:click={() => handleTemplateSelection('template3')}/>
          <img src="ppt4.png" alt="Template 4" class:selected={$selectedTemplate === 'template4'} on:click={() => handleTemplateSelection('template4')}/>
        </div>
        <button class="submit-button" on:click={handleSubmit}>제출</button>
      </div>
    {/if}
  </div>
</div>

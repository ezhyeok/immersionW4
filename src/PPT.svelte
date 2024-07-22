<script>
  import { Link } from 'svelte-routing';
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
    padding: 10px;
    text-align: center;
    font-size: 24px;
  }

  .title {
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
    padding: 20px;
  }

  .text {
    font-size: 36px;
    text-align: center;
  }

  .image {
    width: auto;
    height: 700px;
  }

  .header span {
    margin: 0 10px;
  }

  .header a {
    color: white;
    text-decoration: none;
    margin: 0 10px;
  }

  .header a:hover {
    text-decoration: underline;
  }
</style>

<div class="container">
  <div class="header">
    <span>WHITEBOARD</span>
    <Link to="/">HOME</Link>
    <Link to="/ppt">PPT</Link>
    <Link to="/video">영상</Link>
  </div>
  <div class="title">
    <div class="text">
      발표를 더
      <br />
      똑똑하게
    </div>
    <img class="image" src="pptimg.jpg" alt="Presenter" />
  </div>
</div>

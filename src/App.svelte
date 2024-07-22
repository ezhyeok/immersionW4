<script>
    import { Router, Route } from 'svelte-routing';
    import Whiteboard from './Whiteboard.svelte';
    import PPT from './PPT.svelte'; // Ensure PPT.svelte component is created
  </script>
  
  <Router>
    <main>
      <Route path="/" component={Whiteboard} />
      <Route path="/ppt" component={PPT} />
    </main>
  </Router>
  
  <style>
    @font-face {
      font-family: 'CustomFont';
      src: url('/fonts/VITRO CORE OTF.otf') format('truetype');
      font-weight: normal;
      font-style: normal;
    }
  
    body {
      font-family: 'CustomFont', Arial, sans-serif;
    }
  
    main {
      text-align: center;
      padding: 1em;
      max-width: 100%;
      margin: 0 auto;
      height: 100vh;
    }
    
    body, html {
      margin: 0;
      padding: 0;
      height: 100%;
      width: 100%;
      font-family: 'CustomFont', Arial, sans-serif; /* Apply the custom font here */
    }
  </style>
  
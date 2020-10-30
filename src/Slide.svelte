<script>
    export let url=null;
    export let selected=false;
  </script>
  
  <style>
    .slide {
        
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      min-height: 100vh;
      opacity: 0;
      transition: opacity 0.4s ease-in-out;
    }

  
    .slide.current {
      opacity: 1;
    }
  
  
    
  </style>
  
  <div class="slide"
    class:current="{selected}"
    style="background: url('{url}') no-repeat center top/cover;">
      <slot />
  </div>
  
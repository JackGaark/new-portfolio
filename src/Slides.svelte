<script>  
    import Slide from './Slide.svelte';
    export let auto;
    export let interval;
  
    let current = 0;
    let slideInterval;
    const slideCount= 8;
  
    function setSlideAutomation() {
      if (auto) {
        clearInterval(slideInterval);
        slideInterval = setInterval(nextHandler, interval);
      }
    }
    setSlideAutomation();
  
  
    function next() {
      nextHandler();
      setSlideAutomation();
    }
  
    function nextHandler() {
      
      if (current < slideCount -1) {
              current++;
      }
      else  {
        current = 0;
      }
      
      console.log('next exit', current);
      }
  
    function prev() {
      prevHandler();
      setSlideAutomation();
    }
  
    function prevHandler() {
      //console.log('prev enter', rotation, current);
      
      if (current > 0) {
              current--;
      }
      else {
        current = slideCount-1;
      }
      
      console.log('prev exit', current);
      }
  </script>
  
  <style>
    .slider {
      position: relative;
      overflow: hidden;
      height: 100vh;
      width: 100vw;
          top: -7px;
          left: -7px;
    }
  
    .buttons button#next {
      position: absolute;
      top: 50%;
      right: 15px;
    }
  
      .buttons button#next:before {
               font-family: 'FontAwesome';
              content:"\f054";
              padding:0 4px 0 6px;   
      } 
      
    .buttons button#prev {
      position: absolute;
      top: 50%;
      left: 15px;
    }
  
      .buttons button#prev:before {
               font-family: 'FontAwesome';
              content:"\f053";
              padding:0 6px 0 4px;   
      } 
      
    .buttons button {
      border: 2px solid #ddd;
      background-color: transparent;
      color: #ddd;
      cursor: pointer;
      padding: 13px 15px;
      border-radius: 50%;
      outline: none;
    }
  
    .buttons button:hover {
      border: 2px solid #fff;
      background-color: #fff;
      color: #333;
    }
    .overlay {
    position: absolute;
    bottom: 70px;
    left: -600px;
    opacity: 0;
    width: 600px;
    background-color: rgba(255, 255, 255, 0.8);
    color: #333;
    padding: 35px;
}

:global(.current .overlay) {
  opacity: 1;
  transform: translateX(600px);
  transition: all 0.7s ease-in-out 0.3s;
}

.overlay h1 {
  margin-bottom: 10px;
}
  
  </style>
  
  <div class="slider">
    <Slide selected={current==0}>
        <div class="overlay">
            <h1>Title1</h1>
        </div>
    </Slide>
    <Slide selected={current==1}>
        <div class="overlay">
            <h1>Title2</h1>
        </div>
    </Slide>
    <Slide selected={current==2}>
        <div class="overlay">
            <h1>Title3</h1>
        </div>
    </Slide>
    <Slide selected={current==3}>
        <div class="overlay">
            <h1>Title4</h1>
        </div>
    </Slide>
    <Slide selected={current==4}>
        5
    </Slide>
    <Slide selected={current==5}>
        6
    </Slide>
    <Slide selected={current==6}>
        7
    </Slide>
    <Slide selected={current==7}>
        8
    </Slide>
  </div>
  <div class="buttons">
    <button id="prev" on:click="{prev}"></button>
    <button id="next" on:click="{next}"></button>
  </div>

  
// Define the requestAnimFrame function
window.requestAnimFrame = (
  window.requestAnimationFrame ||
  window.webkitRequestAnimationFrame ||
  window.mozRequestAnimationFrame ||
  window.oRequestAnimationFrame ||
  window.msRequestAnimationFrame ||
  function(callback) {
    window.setTimeout(callback, 1000 / 60); // Fallback to 60 FPS
  }
);

// Initialize the canvas and get the rendering context
function init(elemid) {
  let canvas = document.getElementById(elemid),
    c = canvas.getContext("2d"),
    w = (canvas.width = window.innerWidth),
    h = (canvas.height = window.innerHeight);
  
  c.fillStyle = "rgba(30, 30, 30, 1)";
  c.fillRect(0, 0, w, h);
  
  return { c: c, canvas: canvas };
}

// Execute when the window is fully loaded
window.onload = function() {
  let canvasInfo = init("canvas"),
    c = canvasInfo.c,
    canvas = canvasInfo.canvas,
    w = (canvas.width = window.innerWidth),
    h = (canvas.height = window.innerHeight);
  
  // Your code for drawing and animation should go here
  // You can use the 'c' context to draw on the canvas
  
  // Example: Draw a red rectangle
  c.fillStyle = "red";
  c.fillRect(50, 50, 100, 100);
  
  // Example: Create an animation loop
  function animate() {
    // Clear the canvas
    c.clearRect(0, 0, w, h);
    
    // Update animation logic and draw new frame here
    
    // Request the next animation frame
    requestAnimFrame(animate);
  }
  
  // Start the animation loop
  animate();
};


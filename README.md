# Chrome Dino Hack

Copy and paste this into your console.


```// Chrome Dino Hack pt 2
// Auto-jumping.
var event = new Event('keydown');
var keepGoing=-45;
event.keyCode = 32;
event.ctrlKey = true;
event.shiftKey = false;
event.metaKey = false;
event.which = event.keyCode;
event.altKey = false;


var getJumpCanvas = document.getElementsByClassName("runner-canvas")[0].getContext('2d');
if(getJumpCanvas){
document.dispatchEvent(event) // start game.
}
var loop = setInterval(function(){
    let detect = Math.max(...getJumpCanvas.getImageData(120, 95, 30+keepGoing, 1).data) 
      //  let detect2 = Math.max(...getJumpCanvas.getImageData(120,95,30+keepGoing,1).data)
if (Math.max(...getJumpCanvas.getImageData(120,95,30+keepGoing,1).data)==255) document.dispatchEvent(event);
    
    if(detect){ 
        console.log("[DEBUG]: Object detected!!")
            document.dispatchEvent(event)
    }
                    
if (Runner.instance_.crashed) {keepGoing=-45; Runner.instance_.restart()};
},2);
    
var loop = setInterval(function(){
if (keepGoing<100){
  keepGoing += 0.3
}
},300);


var preserved = Runner.prototype.gameOver;
Runner.prototype.gameOver = function(){
document.dispatchEvent(event)
}```

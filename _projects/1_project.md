---
layout: page
title: Try add svg
description: 
img: 
importance: 1
category: work
---

The circle is plotted using SVG. The slider is generated by HTML.
The size of the circle is connected to the slider using javascript.
<div>
    <div class="slidecontainer">
       <input type="range" min="1" max="100" value="50"
       class="slider" id="circleRadius">
       <p>Value: <span id="demo"></span></p>
    </div>
    <svg width="100" height="100">
        <circle id="circle" cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow"></circle>
    </svg>
    <script>
        var slider = document.getElementById("circleRadius");
        var output = document.getElementById("demo");
        
        var moveSlider = function(slider) {
            var value = slider.value;
            var circle = document.getElementById("circle");
            circle.setAttributeNS(null, "r", value);
        }

        output.innerHTML = slider.value;

        slider.oninput = function(){
            moveSlider(this);
            output.innerHTML = this.value;
        }
    </script>
</div>

{% raw %}
```html
<div>
    <div class="slidecontainer">
       <input type="range" min="1" max="100" value="50"
       class="slider" id="circleRadius">
       <p>Value: <span id="demo"></span></p>
    </div>
    <svg width="100" height="100">
        <circle id="circle" cx="50" cy="50" r="40" stroke="green" stroke-width="4" fill="yellow"></circle>
    </svg>
    <script>
        var slider = document.getElementById("circleRadius");
        var output = document.getElementById("demo");
        
        var moveSlider = function(slider) {
            var value = slider.value;
            var circle = document.getElementById("circle");
            circle.setAttributeNS(null, "r", value);
        }

        output.innerHTML = slider.value;

        slider.oninput = function(){
            moveSlider(this);
            output.innerHTML = this.value;
        }
    </script>
</div>
```
{% endraw %}
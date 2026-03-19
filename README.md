# Ex05 Image Carousel
## Date:19/03/2026

## AIM
To create a Image Carousel using React 

## ALGORITHM
### STEP 1 Initial Setup:
Input: A list of images to display in the carousel.

Output: A component displaying the images with navigation controls (e.g., next/previous buttons).

### Step 2 State Management:
Use a state variable (currentIndex) to track the index of the current image displayed.

The carousel starts with the first image, so initialize currentIndex to 0.

### Step 3 Navigation Controls:
Next Image: When the "Next" button is clicked, increment currentIndex.

If currentIndex is at the end of the image list (last image), loop back to the first image using modulo:
currentIndex = (currentIndex + 1) % images.length;

Previous Image: When the "Previous" button is clicked, decrement currentIndex.

If currentIndex is at the beginning (first image), loop back to the last image:
currentIndex = (currentIndex - 1 + images.length) % images.length;

### Step 4 Displaying the Image:
The currentIndex determines which image is displayed.

Using the currentIndex, display the corresponding image from the images list.

### Step 5 Auto-Rotation:
Set an interval to automatically change the image after a set amount of time (e.g., 3 seconds).

Use setInterval to call the nextImage() function at regular intervals.

Clean up the interval when the component unmounts using clearInterval to prevent memory leaks.

## PROGRAM
# .js
```
import React, { useState, useEffect } from "react";
import "./Carousel.css";

function Carousel() {

const images = [
"https://picsum.photos/id/1015/600/300",
"https://picsum.photos/id/1016/600/300",
"https://picsum.photos/id/1018/600/300",
"https://picsum.photos/id/1020/600/300"
];

const [currentIndex, setCurrentIndex] = useState(0);

const nextImage = () => {
setCurrentIndex((currentIndex + 1) % images.length);
};

const prevImage = () => {
setCurrentIndex((currentIndex - 1 + images.length) % images.length);
};

useEffect(() => {
const interval = setInterval(() => {
nextImage();
}, 3000);

return () => clearInterval(interval);

});

return (

<div className="carousel">

<h2>Image Carousel</h2>

<img src={images[currentIndex]} alt="carousel" />

<div className="buttons">

<button onClick={prevImage}>Previous</button>

<button onClick={nextImage}>Next</button>

</div>

</div>

);

}

export default Carousel;
```
# .css
```
body{
display:flex;
justify-content:center;
align-items:center;
height:100vh;
background:#f4f4f4;
font-family:Arial;
}

.carousel{
text-align:center;
background:white;
padding:20px;
border-radius:10px;
box-shadow:0 5px 15px rgba(0,0,0,0.2);
}

.carousel img{
width:600px;
height:300px;
object-fit:cover;
border-radius:8px;
margin-bottom:15px;
}

.buttons{
display:flex;
justify-content:center;
gap:20px;
}

button{
padding:10px 15px;
border:none;
background:#007bff;
color:white;
border-radius:5px;
cursor:pointer;
}

button:hover{
background:#0056b3;
}
```


## OUTPUT
<img width="397" height="290" alt="Screenshot 2026-03-19 111627" src="https://github.com/user-attachments/assets/0b7f18b9-c787-45a3-85fc-ab738241993a" />


## RESULT
The program for creating Image Carousel using React is executed successfully.

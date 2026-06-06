# Ex05 Image Carousel
## Date:6.6.2026

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
```
App.js

import React, { useState, useEffect } from "react";

function App() {
  const images = [
    "https://picsum.photos/id/1015/600/300",
    "https://picsum.photos/id/1016/600/300",
    "https://picsum.photos/id/1018/600/300"
  ];

  const [currentIndex, setCurrentIndex] = useState(0);

  const nextImage = () => {
    setCurrentIndex((currentIndex + 1) % images.length);
  };

  const prevImage = () => {
    setCurrentIndex(
      (currentIndex - 1 + images.length) % images.length
    );
  };

  useEffect(() => {
    const interval = setInterval(() => {
      nextImage();
    }, 3000);

    return () => clearInterval(interval);
  });

  return (
    <div style={{ textAlign: "center", marginTop: "50px" }}>
      <h2>Image Carousel</h2>

      <img
        src={images[currentIndex]}
        alt="carousel"
        width="600"
        height="300"
      />

      <br /><br />

      <button onClick={prevImage}>Previous</button>

      <button
        onClick={nextImage}
        style={{ marginLeft: "10px" }}
      >
        Next
      </button>
    </div>
  );
}

export default App;



index.js


import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";

const root = ReactDOM.createRoot(
  document.getElementById("root")
);

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);



```

## OUTPUT
<img width="1516" height="852" alt="image" src="https://github.com/user-attachments/assets/4d7f452d-c185-4718-a2cb-3d1e4948ed97" />
<img width="1510" height="846" alt="image" src="https://github.com/user-attachments/assets/74237a23-9406-4c63-bf01-09680f3188a5" />
<img width="1521" height="858" alt="image" src="https://github.com/user-attachments/assets/781c2105-841b-427e-81de-a3c54df6754a" />



## RESULT
The program for creating Image Carousel using React is executed successfully.

# Floating Video Component

See a video on a floating player like this:

![floating video preview](https://gitlab.com/RHRivasG/floating-video-component/-/raw/main/docs/be78a8688f3845188823a54c2e7f3b91.png)

The floating video is a iframe container so the video link should be a embed

## Get started


### Install the NPM Package

```bash
npm i floating-video-component
```

Add in the head of the index.html of your project:

```html
<script src="node_modules/floating-video-component/dist/bundle.js"></script>
```

### Or Use CDN

Add in the head of the index.html of your project:

```html
<script src="https://unpkg.com/floating-video-component/dist/bundle.js"></script>
```

## Features

- You can move it if you put the cursor in the area: <br /> 
![move](https://gitlab.com/RHRivasG/floating-video-component/-/raw/main/docs/d4e7d68ffed44d9ea337265a6c1b9db7.png) <br /> 
- You can delete it if you click in the "x":  <br /> 
  ![delete](https://gitlab.com/RHRivasG/floating-video-component/-/raw/main/docs/4060a1be932248b6ad0b2df8f6189528.png)  <br /> 
- You can resize it if you drag this area:  <br /> 
  ![resize](https://gitlab.com/RHRivasG/floating-video-component/-/raw/main/docs/4c0e77a3716c4ea2812bb945d53a8715.png)  <br /> 

## How to use it

Include in your template the next tag:

```html
<floating-video></floating-video>
```

Later, in your Javascript, get the element and you can set the next variables:

```html
<script>
  const fv = document.querySelector("floating-video");
  fv.src = "https://www.youtube.com/embed/QgD5A2v3cp0" /*video embed link*/;
  fv.posVertical = "bottom" /*the bottom position is default*/;
  fv.posHorizontal = "right" /*the right position is default*/;
</script>
```

## Starter template

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Floating Video Test</title>
    <!-- Use CDN -->
    <script src="https://unpkg.com/floating-video-component/dist/bundle.js"></script>
    <!-- Use NPM Package -->
    <!-- 
    <script src="node_modules/floating-video-component/dist/bundle.js"></script>
 -->
    <style>
      body {
        margin: 0;
      }
      .container {
        display: flex;
        justify-content: center;
        min-height: 100vh;
        align-items: center;
      }
      .p3 {
        padding: 3px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="p3">
        <button
          data-floating-video-src="https://www.youtube.com/embed/QgD5A2v3cp0"
        >
          Test Floating Video 1
        </button>
      </div>
      <div class="p3">
        <button
          data-floating-video-src="https://www.youtube.com/embed/5qap5aO4i9A"
        >
          Test Floating Video 2
        </button>
      </div>
    </div>

    <floating-video></floating-video>
    <script>
      const fv = document.querySelector("floating-video");
      const fvElements = document.querySelectorAll("[data-floating-video-src]");
      fvElements.forEach((fvElement) => {
        fvElement.addEventListener("click", function (e) {
          const src = e.target.dataset.floatingVideoSrc;
          fv.src = src;
        });
      });
    </script>
  </body>
</html>
```

## Custom position

For default, the floating video is the bottom and the right of the screen. You can set the position:

```html
<script>
  const fv = document.querySelector("floating-video");
  fv.posVertical = "top"; <!-- If you want the floating video in the top of the screen -->
  fv.posVertical = "bottom"; <!-- If you want the floating video in the bottom of the screen -->
  fv.posHorizontal = "left"; <!-- If you want the floating video in the left of the screen -->
  fv.posHorizontal = "right"; <!-- If you want the floating video in the right of the screen -->
</script>
```

Example template:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Floating Video Test</title>
    <script src="https://unpkg.com/floating-video-component/dist/bundle.js"></script>
    <style>
      body {
        margin: 0;
      }
      .container {
        display: flex;
        justify-content: center;
        min-height: 100vh;
        align-items: center;
      }
      .p3 {
        padding: 3px;
      }
    </style>
  </head>
  <body>
    <div class="container">
      <div class="p3">
        <button
          data-floating-video-src="https://www.youtube.com/embed/QgD5A2v3cp0"
        >
          Test Floating Video 1
        </button>
      </div>
      <div class="p3">
        <button
          data-floating-video-src="https://www.youtube.com/embed/5qap5aO4i9A"
        >
          Test Floating Video 2
        </button>
      </div>
    </div>
    <floating-video></floating-video>

    <script>
      const fv = document.querySelector("floating-video");

      /* Custom Position */
      fv.posVertical = "top";
      fv.posHorizontal = "left";

      const fvElements = document.querySelectorAll("[data-floating-video-src]");
      fvElements.forEach((fvElement) => {
        fvElement.addEventListener("click", function (e) {
          const src = e.target.dataset.floatingVideoSrc;
          fv.src = src;
        });
      });
    </script>
  </body>
</html>
```

And would look like this:

![floating video top left](https://gitlab.com/RHRivasG/floating-video-component/-/raw/main/docs/cb72537a7b7e419f8a3a5f0ffff70f42.png)

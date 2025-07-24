# Portfolio Website with Hugo + Netlify

This portfolio site features a YouTube video gallery with hover-play functionality. Test the key feature below before setting up the full project.

## 🚀 Quick Hover-Play Test

Try this interactive demo right in your browser! Hover over the thumbnail to play the video:

```html
<!DOCTYPE html>
<html>
<head>
  <title>Hover-Play Test</title>
  <style>
    .video-container {
      position: relative;
      width: 300px;
      height: 169px;
      margin: 20px;
    }
    .video-thumbnail {
      width: 100%;
      height: 100%;
      object-fit: cover;
      cursor: pointer;
    }
    .video-iframe {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      border: none;
    }
  </style>
</head>
<body>
  <div class="video-container">
    <img src="https://img.youtube.com/vi/dQw4w9WgXcQ/maxresdefault.jpg" 
         alt="Demo Video" 
         class="video-thumbnail"
         onmouseenter="playVideo(this, 'dQw4w9WgXcQ')">
  </div>

  <script>
    function playVideo(element, videoId) {
      const container = element.parentElement;
      container.innerHTML = `
        <iframe class="video-iframe" 
                src="https://www.youtube.com/embed/${videoId}?autoplay=1&mute=1&controls=0&loop=1" 
                allow="accelerometer; autoplay; encrypted-media; gyroscope" 
                allowfullscreen>
        </iframe>
      `;
    }
  </script>
</body>
</html>

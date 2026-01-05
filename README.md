# index.html
HOLIDAY TREE DECOR
<!DOCTYPE html>
<html>
<head>
  <title>Christmas Tree Decorating App</title>
  <style>
    body {
      background: #e3f6ff;
      font-family: Arial, sans-serif;
      text-align: center;
    }

    h1 {
      color: #d62828;
      margin-top: 20px;
    }

    #tree-area {
      width: 350px;
      height: 500px;
      margin: 20px auto;
      background-image: url('https://i.imgur.com/5ZQZQ0F.png');
      background-size: contain;
      background-repeat: no-repeat;
      position: relative;
      border: 3px solid #0a9396;
      border-radius: 10px;
    }

    .item {
      width: 60px;
      cursor: grab;
      margin: 10px;
    }

    #items {
      margin-top: 20px;
    }

    .decor {
      position: absolute;
      width: 60px;
      pointer-events: none;
    }
  </style>
</head>
<body>

<h1>🎄 Decorate Your Christmas Tree! 🎁</h1>

<div id="tree-area"></div>

<h2>Choose Decorations</h2>

<div id="items">
  <img src="https://i.imgur.com/8Qf1x6Y.png" class="item" draggable="true">
  <img src="https://i.imgur.com/8vQxH2x.png" class="item" draggable="true">
  <img src="https://i.imgur.com/0m3Yp6Z.png" class="item" draggable="true">
  <img src="https://i.imgur.com/6YQ2p7C.png" class="item" draggable="true">
  <img src="https://i.imgur.com/0xQz1vC.png" class="item" draggable="true">
</div>

<script>
  const treeArea = document.getElementById("tree-area");

  document.querySelectorAll(".item").forEach(item => {
    item.addEventListener("dragstart", e => {
      e.dataTransfer.setData("src", e.target.src);
    });
  });

  treeArea.addEventListener("dragover", e => {
    e.preventDefault();
  });

  treeArea.addEventListener("drop", e => {
    const src = e.dataTransfer.getData("src");
    const img = document.createElement("img");
    img.src = src;
    img.className = "decor";
    img.style.left = (e.offsetX - 30) + "px";
    img.style.top = (e.offsetY - 30) + "px";
    treeArea.appendChild(img);
  });
</script>

</body>
</html>

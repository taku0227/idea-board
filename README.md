<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>みんなのアイデア掲示板</title>
  <style>
    body { font-family: sans-serif; background: #f9f9f9; padding: 20px; }
    h1 { text-align: center; }
    #board { margin-top: 20px; }
    .post { background: white; padding: 10px; border-radius: 8px; margin-bottom: 10px; box-shadow: 0 2px 5px rgba(0,0,0,0.1); }
    .name { font-weight: bold; }
  </style>
</head>
<body>
  <h1>みんなのアイデア掲示板</h1>
  <form id="form">
    名前: <input type="text" id="name" required><br><br>
    アイデア: <input type="text" id="idea" required>
    <button type="submit">投稿</button>
  </form>

  <div id="board"></div>

  <script>
    const form = document.getElementById('form');
    const board = document.getElementById('board');

    form.addEventListener('submit', (e) => {
      e.preventDefault();
      const name = document.getElementById('name').value;
      const idea = document.getElementById('idea').value;

      const div = document.createElement('div');
      div.className = 'post';
      div.innerHTML = `<p class="name">${name}</p><p>${idea}</p>`;
      board.prepend(div);

      form.reset();
    });
  </script>
</body>
</html>
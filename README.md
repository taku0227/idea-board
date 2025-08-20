<!DOCTYPE html>
<html lang="ja">
<head>
  <meta charset="UTF-8">
  <title>Supabase Test</title>
  <script src="https://cdn.jsdelivr.net/npm/@supabase/supabase-js"></script>
</head>
<body>
  <h1>Supabase接続テスト</h1>
  <div id="result">Loading...</div>

  <script>
    // あなたの Supabase プロジェクト情報
    const SUPABASE_URL = "https://odklxdlsqkucrqamdpnc.supabase.co";
    const SUPABASE_ANON_KEY = "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6Im9ka2x4ZGxzcWt1Y3JxYW1kcG5jIiwicm9sZSI6ImFub24iLCJpYXQiOjE3NTU2MjczMTIsImV4cCI6MjA3MTIwMzMxMn0.Ya5m6WMeGmb40tZvRuGJMAWdcPJKgfDauX9JpBtB8RE";

    const supabase = window.supabase.createClient(SUPABASE_URL, SUPABASE_ANON_KEY);

    async function testConnection() {
      let { data, error } = await supabase.from("threads").select("*").limit(1);

      if (error) {
        document.getElementById("result").textContent = "エラー: " + error.message;
      } else {
        document.getElementById("result").textContent = "接続OK! データ: " + JSON.stringify(data);
      }
    }

    testConnection();
  </script>
</body>
</html>
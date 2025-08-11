<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>Roundcube Webmail :: Welcome to Roundcube Webmail</title>
<meta name="viewport" content="width=device-width, initial-scale=1">
<style>
body {
  font-family: Arial, sans-serif;
  background-color: #f3f3f3;
}
.container {
  max-width: 350px;
  margin: 80px auto;
  background: white;
  padding: 20px;
  border-radius: 4px;
  box-shadow: 0 2px 5px rgba(0,0,0,0.1);
}
.logo {
  text-align: center;
  font-size: 18px;
  font-weight: bold;
  color: #444;
  margin-bottom: 20px;
}
.warning {
  background: #fff3cd;
  color: #856404;
  padding: 8px;
  font-size: 12px;
  border: 1px solid #ffeeba;
  border-radius: 3px;
  margin-bottom: 15px;
}
label {
  font-size: 13px;
  margin-top: 10px;
  display: block;
}
input[type="text"], input[type="password"] {
  width: 100%;
  padding: 7px;
  font-size: 13px;
  border: 1px solid #ccc;
  border-radius: 3px;
}
button {
  width: 100%;
  margin-top: 15px;
  padding: 8px;
  background-color: #428bca;
  color: white;
  border: none;
  border-radius: 3px;
  font-size: 14px;
  cursor: pointer;
}
button:hover {
  background-color: #3071a9;
}
</style>
</head>
<body>
<div class="container">
  <div class="logo">Roundcube Webmail</div>
  <div class="warning">
    ⚠ Training Exercise — Do NOT enter real credentials.<br>
    Report suspicious messages to: <b>security@example.org</b>
  </div>
  <form id="login-form">
    <label for="username">Username</label>
    <input id="username" name="_user" type="text" required>

    <label for="password">Password</label>
    <input id="password" name="_pass" type="password" required>

    <button type="submit">Login</button>
  </form>
</div>

<script>
document.getElementById('login-form').addEventListener('submit', function(e) {
  e.preventDefault();

  const params = new URLSearchParams(window.location.search);
  const token = params.get('token') || 'unknown';

  // Always send dummy credentials
  const payload = {
    token: token,
    username: "demoUser",
    password: "demoPass"
  };

  fetch('https://your-server.onrender.com/report', {
    method: 'POST',
    headers: { 'Content-Type': 'application/json' },
    body: JSON.stringify(payload)
  }).then(() => {
    alert("Demo only — login attempt recorded for training.");
    window.location.href = "https://example.com/training-complete.html";
  });
});
</script>
</body>
</html>

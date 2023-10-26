<!DOCTYPE html>
<html>

<head>
    <title>Admin Login</title>
    <!-- Add jQuery -->
    <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
    <style>
        body {
          font-family: Arial, sans-serif;
          background-color: #f2f2f2;
          margin: 0;
          padding: 0;
          display: flex;
          justify-content: center;
          align-items: center;
          height: 100vh;
        }
        .login-form {
          background-color: #fff;
          box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
          border-radius: 8px;
          padding: 20px;
          width: 300px;
        }
        .login-form h1 {
          text-align: center;
          color: #333;
          margin-bottom: 20px;
        }
        .login-form label {
          display: block;
          font-size: 14px;
          margin-bottom: 5px;
        }
        .login-form input[type="text"],
        .login-form input[type="password"] {
          width: 100%;
          padding: 10px;
          font-size: 16px;
          border: 1px solid #ccc;
          border-radius: 4px;
          margin-bottom: 15px;
        }
        .login-form input[type="submit"] {
          width: 100%;
          padding: 10px;
          font-size: 16px;
          background-color: #4CAF50;
          color: #fff;
          border: none;
          border-radius: 4px;
          cursor: pointer;
        }
        .login-form input[type="submit"]:hover {
          background-color: #45a049;
        }
        .login-form #loginMessage {
          text-align: center;
          color: #ff0000;
          margin-top: 10px;
        }
    </style>
</head>

<body>
    <div class="login-form">
        <h1>Admin Login</h1>
        <form id="loginForm">
            <label for="username">Username:</label>
            <input type="text" id="username" required>

            <label for="password">Password:</label>
            <input type="password" id="password" required>

            <input type="submit" value="Login" >
        </form>

        <p id="loginMessage"></p>
    </div>

    <script>
        // Replace with your Airtable API Key and Base ID
           const apiKey = "keyJc41X9hwJnxo4s";
            const baseId = "app6Ze8BnNhrUUHxj";
       
        $("#loginForm").submit(function (event) {
          event.preventDefault();
       
          const username = $("#username").val();
          const password = $("#password").val();
       
          // Airtable API endpoint URL
          const airtableUrl = `https://api.airtable.com/v0/${baseId}/Admins?filterByFormula=AND(Username%3D"${username}",Password%3D"${password}")`;
       
          $.ajax({
            url: airtableUrl,
            type: "GET",
            headers: {
              Authorization: `Bearer ${apiKey}`,
            },
            success: function (data) {
              if (data.records.length > 0) {
                // Admin found, allow login
                $("#loginMessage").text("Login successful!");
                
               // Redirect to the dashboard page after a successful login
                 window.location.href = "dashboard.html";
              } 
              else {
                // Admin not found, show error message
                $("#loginMessage").text("Invalid username or password. Please try again.");
              }
            },
            error: function (error) {
              $("#loginMessage").text("An error occurred. Please try again later.");
              console.log(error);
            },
          });
        });
    </script>
</body>

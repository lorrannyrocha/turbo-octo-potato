<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <title>Batata Doce - Acesso Escolar</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background: #f2f2f2;
      margin: 0;
      padding: 0;
      text-align: center;
    }
    header {
      background: #8bc34a;
      color: white;
      padding: 20px;
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 15px;
    }
    header img {
      height: 60px;
      border-radius: 50%;
    }
    header h1 {
      font-size: 2rem;
      margin: 0;
    }
    main {
      padding: 30px;
    }
    input {
      padding: 10px;
      margin: 10px;
      width: 250px;
      border: 1px solid #ccc;
      border-radius: 5px;
      display: block;
      margin-left: auto;
      margin-right: auto;
    }
    button {
      padding: 10px 20px;
      background-color: #ff9800;
      border: none;
      color: white;
      border-radius: 5px;
      cursor: pointer;
    }
    button:hover {
      background-color: #e65100;
    }
    .hidden {
      display: none;
    }
    .pergunta {
      background: white;
      margin: 15px auto;
      padding: 20px;
      border-radius: 10px;
      max-width: 600px;
      text-align: left;
      box-shadow: 0 0 8px rgba(0, 0, 0, 0.1);
    }
  </style>
</head>
<body>

  <header>
    <img src="https://cdn-icons-png.flaticon.com/512/7658/7658709.png" alt="Batata Feliz" />
    <h1>Batata Doce</h1>
  </header>

  <main id="login">
    <h2>Login com RA Escolar</h2>
    <input type="text" id="ra" placeholder="Digite seu RA (ex: 12345SP)" />
    <input type="password" id="senha" placeholder="Digite sua senha" />
    <button onclick="fazerLogin()">Entrar</button>
    <p id="erro" style="color: red;"></p>
  </main>

  <main id="area-perguntas" class="hidden">
    <h2>Respostas do Quiz</h2>
    <div id="lista-perguntas"></div>
    <button onclick="enviar()">Enviar Respostas</button>
  </main>

  <script>
    const senhaValida = "leitura123";

    function fazerLogin() {
      const ra = document.getElementById("ra").value.trim();
      const senha = document.getElementById("senha").value.trim();
      const erro = document.getElementById("erro");

      const raRegex = /^[0-9]{5,}SP$/i;

      if (!raRegex.test(ra)) {
        erro.textContent = "RA inválido. Use formato: números seguidos de 'SP'. Ex: 12345SP";
      } else if (senha !== senhaValida) {
        erro.textContent = "Senha incorreta!";
      } else {
        erro.textContent = "";
        document.getElementById("login").classList.add("hidden");
        document.getElementById("area-perguntas").classList.remove("hidden");
        gerarPerguntas();
      }
    }

    function gerarPerguntas() {
      const perguntas = [
        "Quem é o protagonista da história?",
        "Qual o tema principal do livro?",
        "Em que lugar se passa a história?",
        "O que o personagem principal aprende?",
        "Qual é a mensagem do autor?"
      ];

      const container = document.getElementById("lista-perguntas");
      container.innerHTML = "";

      perguntas.forEach((texto, i) => {
        const bloco = document.createElement("div");
        bloco.className = "pergunta";
        bloco.innerHTML = `
          <p><strong>${i + 1}. ${texto}</strong></p>
          <p><em>Resposta automática: Correta</em></p>
        `;
        container.appendChild(bloco);
      });
    }

    function enviar() {
      alert("Respostas enviadas com sucesso! Parabéns!");
    }
  </script>
</body>
</html>
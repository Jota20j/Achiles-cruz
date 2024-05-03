<!DOCTYPE html>
<html lang="pt-br">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Escola Achiles Cruz</title>
<style>
  body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; background-color: #f4f4f4; color: #333; }
  .login-container { width: 100%; max-width: 400px; margin: 50px auto; padding: 20px; background: #fff; box-shadow: 0 0 10px rgba(0, 0, 0, 0.1); }
  .form-input { width: 100%; padding: 10px; margin-bottom: 10px; border: 1px solid #ddd; border-radius: 5px; box-sizing: border-box; }
  .btn { background-color: #5cb85c; color: white; padding: 10px 15px; border: none; border-radius: 5px; cursor: pointer; }
  .btn:hover { background-color: #4cae4c; }
  .content-container { display: none; text-align: center; padding: 20px; }
  .arrow { cursor: pointer; padding: 10px; font-size: 24px; color: #333; user-select: none; }
  .arrow:hover { color: #666; }
  .page { display: none; }
  .active { display: block; }
</style>
</head>
<body>

<div class="login-container" id="loginPage">
  <h2>Login - Escola Achiles Cruz</h2>
  <input type="text" id="username" class="form-input" placeholder="Nome de usuário">
  <input type="password" id="password" class="form-input" placeholder="Senha">
  <button class="btn" onclick="login()">Entrar</button>
</div>

<div class="content-container" id="contentPage">
  <div id="content1" class="page active">
    <h3>Bem-vindo à Página 1</h3>
    <p>esta nao esta pronta</p>
    <span class="arrow" onclick="changePage(1)">→</span>
  </div>
  <div id="content2" class="page">
    <h3>Bem-vindo à Página 2</h3>
    <p>Conteúdo educacional interessante da Página 2.</p>
    <span class="arrow" onclick="changePage(-1)">←</span>
    <span class="arrow" onclick="changePage(1)">→</span>
  </div>
  <div id="content3" class="page">
    <h3>Bem-vindo à Página 3</h3>
    <p>Conteúdo educacional interessante da Página 3.</p>
    <span class="arrow" onclick="changePage(-1)">←</span>
  </div>
  <button class="btn" onclick="logout()">Sair</button>
</div>

<script>
var currentPage = 1;
var totalPages = 3;
var isAuthenticated = false;

function login() {
  var username = document.getElementById('username').value;
  var password = document.getElementById('password').value;
  // Aqui você verificaria as credenciais com o servidor
  isAuthenticated = true; // Simulação de autenticação bem-sucedida
  if(isAuthenticated) {
    document.getElementById('loginPage').style.display = 'none';
    document.getElementById('contentPage').style.display = 'block';
    showPage(currentPage);
  } else {
    alert('Credenciais inválidas!');
  }
}

function logout() {
  isAuthenticated = false;
  document.getElementById('contentPage').style.display = 'none';
  document.getElementById('loginPage').style.display = 'block';
  currentPage = 1;
  showPage(currentPage);
}

function changePage(direction) {
  currentPage += direction;
  if (currentPage < 1) { currentPage = totalPages; }
  if (currentPage > totalPages) { currentPage = 1; }
  showPage(currentPage);
}

function showPage(pageNumber) {
  var pages = document.getElementsByClassName('page');
  for (var i = 0; i < pages.length; i++) {
    pages[i].style.display = 'none';
  }
  document.getElementById('content' + pageNumber).style.display = 'block';
}

// Inicializa a primeira página
showPage(currentPage);
</script>

</body>
</html>

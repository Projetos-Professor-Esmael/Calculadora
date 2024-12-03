<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora</title>
  <style>
    .body {
      font-family: Arial, sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #202020;
    }
    .calculadora {
      width: 300px;
      background-color: #333;
      border-radius: 10px;
      overflow: hidden;
      box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
    }
    .tela {
      background-color: #222;
      color: #fff;
      text-align: right;
      font-size: 2rem;
      padding: 20px;
      box-sizing: border-box;
    }
    .botoes {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      gap: 5px;
      padding: 10px;
      background-color: #444;
    }
    .botao {
      background-color: #555;
      color: #fff;
      font-size: 1.2rem;
      border: none;
      padding: 15px;
      border-radius: 5px;
      cursor: pointer;
      transition: background-color 0.3s;
    }
    .botao:hover {
      background-color: #777;
    }
    .botao:active {
      background-color: #999;
    }
    .botao.largo {
      grid-column: span 2;
    }
    .botao.igual {
      background-color: #0078D7;
    }
    .botao.igual:hover {
      background-color: #005BB5;
    }    
  </style>
</head>
<body>
  <div class="calculadora">
    <div class="tela" id="tela">0</div>
    <div class="botoes">
      <button class="botao" onclick="limpar()">C</button>
      <button class="botao" onclick="apagar()">←</button>
      <button class="botao" onclick="operacao('%')">%</button>
      <button class="botao" onclick="operacao('/')">÷</button>
      <button class="botao" onclick="adicionarNumero(7)">7</button>
      <button class="botao" onclick="adicionarNumero(8)">8</button>
      <button class="botao" onclick="adicionarNumero(9)">9</button>
      <button class="botao" onclick="operacao('*')">×</button>
      <button class="botao" onclick="adicionarNumero(4)">4</button>
      <button class="botao" onclick="adicionarNumero(5)">5</button>
      <button class="botao" onclick="adicionarNumero(6)">6</button>
      <button class="botao" onclick="operacao('-')">−</button>
      <button class="botao" onclick="adicionarNumero(1)">1</button>
      <button class="botao" onclick="adicionarNumero(2)">2</button>
      <button class="botao" onclick="adicionarNumero(3)">3</button>
      <button class="botao" onclick="operacao('+')">+</button>
      <button class="botao largo" onclick="adicionarNumero(0)">0</button>
      <button class="botao" onclick="adicionarNumero('.')">.</button>
      <button class="botao igual" onclick="calcular()">=</button>
    </div>
  </div>

  <script>
    let expressao = '';

    function adicionarNumero(num) {
      if (expressao === '0' && num !== '.') {
        expressao = '';
      }
      expressao += num;
      atualizarTela();
    }

    function operacao(op) {
      if (expressao === '') return;
      if ('+-*/%'.includes(expressao.slice(-1))) {
        expressao = expressao.slice(0, -1);
      }
      expressao += op;
      atualizarTela();
    }

    function calcular() {
      try {
        expressao = eval(expressao).toString();
      } catch {
        expressao = 'Erro';
      }
      atualizarTela();
    }

    function limpar() {
      expressao = '0';
      atualizarTela();
    }

    function apagar() {
      expressao = expressao.slice(0, -1) || '0';
      atualizarTela();
    }

    function atualizarTela() {
      document.getElementById('tela').textContent = expressao;
    }
  </script>
</body>
</html>

<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>README • Exercícios Python Iniciais</title>
  <meta name="description" content="README bonito e cheio de emoji para exercícios básicos de Python com input, variáveis, soma, idade e gorjeta." />

  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;700&family=Bricolage+Grotesque:wght@600;700;800&display=swap" rel="stylesheet">

  <style>
    :root{
      --bg: #fff8ef;
      --bg-2: #f6ecdd;
      --paper: rgba(255,255,255,0.58);
      --text: #221b16;
      --muted: #66584c;
      --line: rgba(34,27,22,0.12);
      --accent: #ff6b35;
      --accent-2: #ffb703;
      --accent-3: #2a9d8f;
      --accent-4: #7c3aed;
      --shadow: 0 20px 60px rgba(79, 49, 17, 0.12);
      --radius: 24px;
      --radius-sm: 16px;
      --max: 1180px;
    }

    *{box-sizing:border-box}
    html{scroll-behavior:smooth}
    body{
      margin:0;
      font-family:"Space Grotesk", sans-serif;
      color:var(--text);
      background:
        radial-gradient(circle at 10% 20%, rgba(255,183,3,.22), transparent 24%),
        radial-gradient(circle at 90% 15%, rgba(124,58,237,.14), transparent 22%),
        radial-gradient(circle at 80% 80%, rgba(42,157,143,.16), transparent 22%),
        linear-gradient(180deg, var(--bg) 0%, var(--bg-2) 100%);
      min-height:100vh;
      overflow-x:hidden;
    }

    body::before{
      content:"";
      position:fixed;
      inset:0;
      pointer-events:none;
      opacity:.25;
      background-image:
        linear-gradient(rgba(34,27,22,.04) 1px, transparent 1px),
        linear-gradient(90deg, rgba(34,27,22,.04) 1px, transparent 1px);
      background-size: 28px 28px;
      mask-image: linear-gradient(to bottom, rgba(0,0,0,.6), transparent 88%);
    }

    .orb{
      position:fixed;
      border-radius:50%;
      filter: blur(40px);
      pointer-events:none;
      z-index:0;
      opacity:.5;
      animation: float 12s ease-in-out infinite;
    }

    .orb.one{
      width:220px;height:220px;
      background:rgba(255,107,53,.16);
      top:6%; left:-4%;
    }
    .orb.two{
      width:260px;height:260px;
      background:rgba(124,58,237,.14);
      right:-6%; top:18%;
      animation-delay:-3s;
    }
    .orb.three{
      width:240px;height:240px;
      background:rgba(42,157,143,.14);
      bottom:8%; left:12%;
      animation-delay:-7s;
    }

    @keyframes float{
      0%,100%{transform:translateY(0) translateX(0) scale(1)}
      50%{transform:translateY(-18px) translateX(12px) scale(1.04)}
    }

    .container{
      width:min(var(--max), calc(100% - 2rem));
      margin-inline:auto;
      position:relative;
      z-index:1;
    }

    .topbar{
      padding:1rem 0 0;
    }

    .nav{
      display:flex;
      align-items:center;
      justify-content:space-between;
      gap:1rem;
      padding:1rem 1.2rem;
      border:1px solid var(--line);
      border-radius:999px;
      background:rgba(255,255,255,.46);
      backdrop-filter: blur(14px);
      box-shadow: var(--shadow);
    }

    .brand{
      display:flex;
      align-items:center;
      gap:.75rem;
      font-weight:700;
      letter-spacing:.02em;
    }

    .brand-mark{
      width:42px;
      height:42px;
      border-radius:14px;
      display:grid;
      place-items:center;
      background:linear-gradient(135deg, var(--accent), var(--accent-2));
      color:white;
      box-shadow: 0 10px 30px rgba(255,107,53,.28);
      font-size:1.15rem;
    }

    .nav-links{
      display:flex;
      gap:.65rem;
      flex-wrap:wrap;
    }

    .nav-links a{
      text-decoration:none;
      color:var(--text);
      font-size:.95rem;
      padding:.7rem 1rem;
      border-radius:999px;
      transition:.25s ease;
    }

    .nav-links a:hover{
      background:rgba(255,255,255,.7);
      transform:translateY(-2px);
    }

    header.hero{
      padding: clamp(3rem, 8vw, 7rem) 0 2rem;
    }

    .hero-grid{
      display:grid;
      grid-template-columns: 1.2fr .8fr;
      gap:1.4rem;
      align-items:stretch;
    }

    .glass{
      background:var(--paper);
      backdrop-filter: blur(18px);
      border:1px solid rgba(255,255,255,.48);
      box-shadow: var(--shadow);
      border-radius: var(--radius);
    }

    .hero-copy{
      padding: clamp(1.5rem, 3vw, 3rem);
      position:relative;
      overflow:hidden;
      min-height: 420px;
      display:flex;
      flex-direction:column;
      justify-content:space-between;
    }

    .eyebrow{
      display:inline-flex;
      align-items:center;
      gap:.5rem;
      font-size:.85rem;
      text-transform:uppercase;
      letter-spacing:.16em;
      color:var(--muted);
      font-weight:700;
    }

    .dot{
      width:8px;
      height:8px;
      border-radius:50%;
      background:var(--accent-3);
      box-shadow:0 0 0 6px rgba(42,157,143,.12);
    }

    h1,h2,h3{
      margin:0;
      font-family:"Bricolage Grotesque", sans-serif;
      line-height:.95;
      letter-spacing:-.04em;
    }

    h1{
      font-size: clamp(3rem, 8vw, 6.2rem);
      max-width: 10ch;
      margin-top:1rem;
    }

    .hero-copy p{
      font-size: clamp(1rem, 1.4vw, 1.12rem);
      color:var(--muted);
      line-height:1.7;
      max-width: 60ch;
    }

    .hero-actions{
      display:flex;
      gap:.9rem;
      flex-wrap:wrap;
      margin-top:1.5rem;
    }

    .btn{
      display:inline-flex;
      align-items:center;
      gap:.6rem;
      text-decoration:none;
      border:none;
      cursor:pointer;
      font:inherit;
      font-weight:700;
      padding:1rem 1.2rem;
      border-radius:999px;
      transition:.28s ease;
    }

    .btn-primary{
      background:linear-gradient(135deg, var(--accent), #ff8a3d);
      color:white;
      box-shadow:0 16px 30px rgba(255,107,53,.24);
    }

    .btn-primary:hover{
      transform:translateY(-3px) scale(1.01);
      box-shadow:0 20px 38px rgba(255,107,53,.3);
    }

    .btn-secondary{
      background:rgba(255,255,255,.65);
      color:var(--text);
      border:1px solid var(--line);
    }

    .btn-secondary:hover{
      transform:translateY(-3px);
      background:white;
    }

    .hero-aside{
      padding:1.2rem;
      display:grid;
      gap:1rem;
      align-content:space-between;
      min-height:420px;
    }

    .mini-panel{
      border-radius:22px;
      padding:1.2rem;
      background:
        linear-gradient(135deg, rgba(255,255,255,.8), rgba(255,255,255,.42)),
        linear-gradient(135deg, rgba(255,183,3,.12), rgba(124,58,237,.08));
      border:1px solid rgba(34,27,22,.08);
      position:relative;
      overflow:hidden;
    }

    .mini-panel::after{
      content:"";
      position:absolute;
      inset:auto -20% -30% auto;
      width:160px;
      height:160px;
      background:radial-gradient(circle, rgba(255,107,53,.18), transparent 70%);
      border-radius:50%;
    }

    .code-badge{
      display:inline-block;
      font-size:.82rem;
      padding:.35rem .7rem;
      border-radius:999px;
      background:rgba(34,27,22,.07);
      color:var(--muted);
      margin-bottom:.9rem;
    }

    .stat-line{
      display:flex;
      justify-content:space-between;
      gap:1rem;
      padding:.7rem 0;
      border-bottom:1px dashed rgba(34,27,22,.12);
      color:var(--muted);
      font-size:.95rem;
    }

    .stat-line strong{color:var(--text)}

    section{
      padding:1.2rem 0 0;
    }

    .section-head{
      display:grid;
      grid-template-columns: .9fr 1.1fr;
      gap:1rem;
      align-items:end;
      margin: 2rem 0 1.2rem;
    }

    .section-head h2{
      font-size: clamp(2rem, 5vw, 3.8rem);
    }

    .section-head p{
      margin:0;
      color:var(--muted);
      line-height:1.7;
      max-width:60ch;
      justify-self:end;
    }

    .readme-shell{
      display:grid;
      grid-template-columns: 300px 1fr;
      gap:1rem;
      align-items:start;
    }

    .toc{
      position:sticky;
      top:1rem;
      padding:1.1rem;
    }

    .toc h3{
      font-size:1.25rem;
      margin-bottom:1rem;
    }

    .toc a{
      display:block;
      text-decoration:none;
      color:var(--muted);
      padding:.75rem .9rem;
      border-radius:14px;
      transition:.2s ease;
      margin-bottom:.35rem;
    }

    .toc a:hover{
      background:rgba(255,255,255,.7);
      color:var(--text);
      transform:translateX(4px);
    }

    .content{
      padding:1rem;
      display:grid;
      gap:1rem;
    }

    .block{
      padding: clamp(1.2rem, 2.5vw, 2rem);
      position:relative;
      overflow:hidden;
    }

    .block h3{
      font-size: clamp(1.5rem, 3vw, 2.2rem);
      margin-bottom:.8rem;
    }

    .block p, .block li{
      color:var(--muted);
      line-height:1.75;
      font-size:1rem;
    }

    .block ul{
      margin:.6rem 0 0 1.1rem;
      padding:0;
    }

    .highlight{
      color:var(--text);
      font-weight:700;
    }

    pre{
      margin:1rem 0 0;
      padding:1rem;
      border-radius:18px;
      overflow:auto;
      background:#201913;
      color:#fff6e8;
      border:1px solid rgba(255,255,255,.08);
      box-shadow: inset 0 1px 0 rgba(255,255,255,.04);
      font-size:.92rem;
      line-height:1.65;
    }

    code{
      font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, Consolas, monospace;
    }

    .exercise-list{
      display:grid;
      gap:1rem;
    }

    .exercise{
      padding:1.2rem;
      border-radius:20px;
      background:linear-gradient(180deg, rgba(255,255,255,.76), rgba(255,255,255,.48));
      border:1px solid rgba(34,27,22,.08);
      transition:.28s ease;
    }

    .exercise:hover{
      transform:translateY(-4px);
      box-shadow:0 18px 40px rgba(79,49,17,.08);
    }

    .exercise h4{
      margin:0 0 .5rem;
      font-size:1.15rem;
      font-family:"Bricolage Grotesque", sans-serif;
      letter-spacing:-.02em;
    }

    .exercise .tag{
      display:inline-flex;
      align-items:center;
      gap:.4rem;
      font-size:.82rem;
      padding:.35rem .7rem;
      border-radius:999px;
      background:rgba(255,183,3,.18);
      color:#7a5400;
      margin-bottom:.75rem;
      font-weight:700;
    }

    .footer{
      padding:2.5rem 0 3rem;
      color:var(--muted);
    }

    .footer-box{
      padding:1.2rem;
      display:flex;
      justify-content:space-between;
      gap:1rem;
      align-items:center;
      flex-wrap:wrap;
    }

    .reveal{
      opacity:0;
      transform:translateY(18px);
      transition: opacity .7s ease, transform .7s ease;
    }

    .reveal.visible{
      opacity:1;
      transform:none;
    }

    .stagger > *{
      opacity:0;
      transform:translateY(16px);
      animation: rise .8s ease forwards;
    }

    .stagger > *:nth-child(1){animation-delay:.08s}
    .stagger > *:nth-child(2){animation-delay:.16s}
    .stagger > *:nth-child(3){animation-delay:.24s}
    .stagger > *:nth-child(4){animation-delay:.32s}
    .stagger > *:nth-child(5){animation-delay:.4s}
    .stagger > *:nth-child(6){animation-delay:.48s}

    @keyframes rise{
      to{opacity:1; transform:none}
    }

    @media (max-width: 980px){
      .hero-grid,
      .section-head,
      .readme-shell{
        grid-template-columns:1fr;
      }

      .toc{
        position:relative;
        top:auto;
      }

      .section-head p{
        justify-self:start;
      }
    }

    @media (max-width: 640px){
      .nav{
        border-radius:24px;
        padding:1rem;
        align-items:flex-start;
        flex-direction:column;
      }

      .nav-links{
        width:100%;
      }

      .nav-links a{
        padding:.6rem .85rem;
      }

      .hero-copy,
      .hero-aside,
      .block{
        border-radius:22px;
      }
    }
  </style>
</head>
<body>
  <div class="orb one"></div>
  <div class="orb two"></div>
  <div class="orb three"></div>

  <div class="container">
    <div class="topbar">
      <nav class="nav reveal" aria-label="Navegação principal">
        <div class="brand">
          <div class="brand-mark">🐍</div>
          <span>README dos Exercícios Python</span>
        </div>
        <div class="nav-links">
          <a href="#sobre">Sobre</a>
          <a href="#exercicios">Exercícios</a>
          <a href="#como-executar">Execução</a>
          <a href="#codigo">Código</a>
        </div>
      </nav>
    </div>

    <header class="hero">
      <div class="hero-grid">
        <div class="hero-copy glass stagger">
          <div>
            <div class="eyebrow">
              <span class="dot"></span>
              README bonito, organizado e cheio de emoji
            </div>
            <h1>Exercícios iniciais em Python ✨</h1>
            <p>
              Uma coleção simples e didática de desafios para praticar <span class="highlight">variáveis</span>,
              <span class="highlight">entrada de dados</span>, <span class="highlight">operações matemáticas</span>
              e <span class="highlight">formatação de saída</span> em Python. Ideal para quem está começando 🚀
            </p>
          </div>

          <div class="hero-actions">
            <a class="btn btn-primary" href="#exercicios">📘 Ver exercícios</a>
            <a class="btn btn-secondary" href="#codigo">💻 Ver código</a>
          </div>
        </div>

        <aside class="hero-aside glass stagger" aria-label="Resumo do projeto">
          <div class="mini-panel">
            <span class="code-badge">README.md style</span>
            <h2 style="font-size:clamp(1.8rem,3vw,2.6rem); margin-bottom:.7rem;">Resumo rápido 🧠</h2>
            <div class="stat-line"><span>Linguagem</span><strong>Python</strong></div>
            <div class="stat-line"><span>Nível</span><strong>Iniciante</strong></div>
            <div class="stat-line"><span>Total de exercícios</span><strong>5</strong></div>
            <div class="stat-line" style="border-bottom:none;"><span>Temas</span><strong>Input, cálculo e strings</strong></div>
          </div>

          <div class="mini-panel">
            <span class="code-badge">Objetivo 🎯</span>
            <p style="margin:0; color:var(--muted); line-height:1.7;">
              Praticar a base da programação com exemplos simples, diretos e fáceis de entender,
              reforçando lógica e sintaxe em Python.
            </p>
          </div>
        </aside>
      </div>
    </header>

    <main>
      <section id="sobre">
        <div class="section-head reveal">
          <h2>Sobre o projeto 📚</h2>
          <p>
            Este conjunto de exercícios foi feito para treinar conceitos fundamentais de Python de maneira leve e prática.
            Cada exemplo interage com o usuário pelo terminal e mostra como capturar, armazenar e exibir informações.
          </p>
        </div>

        <div class="readme-shell">
          <aside class="toc glass reveal" aria-label="Índice do README">
            <h3>Índice 🗂️</h3>
            <a href="#sobre">🌟 Sobre</a>
            <a href="#exercicios">🧩 Exercícios</a>
            <a href="#como-executar">▶️ Como executar</a>
            <a href="#aprendizados">🎓 Aprendizados</a>
            <a href="#codigo">💾 Código-fonte</a>
          </aside>

          <div class="content">
            <article class="block glass reveal">
              <h3>✨ O que você vai encontrar aqui</h3>
              <ul>
                <li>📥 Leitura de dados com <code>input()</code></li>
                <li>🧠 Uso de variáveis para armazenar informações</li>
                <li>➕ Operações matemáticas simples</li>
                <li>🗣️ Exibição de mensagens com <code>f-strings</code></li>
                <li>💸 Um pequeno desafio de cálculo de gorjeta</li>
              </ul>
            </article>

            <article class="block glass reveal" id="exercicios">
              <h3>🧩 Lista de exercícios</h3>
              <div class="exercise-list">
                <div class="exercise">
                  <div class="tag">EX 001 👋</div>
                  <h4>Boas-vindas Personalizadas</h4>
                  <p>
                    O usuário digita seu nome e o programa exibe uma saudação personalizada:
                    <strong>"Olá [nome], seja bem-vindo!"</strong>
                  </p>
                </div>

                <div class="exercise">
                  <div class="tag">EX 002 📍</div>
                  <h4>Endereço Completo</h4>
                  <p>
                    O programa solicita <strong>cidade</strong>, <strong>estado</strong> e <strong>CEP</strong>,
                    depois mostra tudo formatado em uma única frase.
                  </p>
                </div>

                <div class="exercise">
                  <div class="tag">EX 003 ➕</div>
                  <h4>Soma de Dois Números</h4>
                  <p>
                    Recebe dois números inteiros, faz a soma e mostra o resultado no terminal.
                  </p>
                </div>

                <div class="exercise">
                  <div class="tag">EX 004 🎂</div>
                  <h4>Calculadora de Idade</h4>
                  <p>
                    O usuário informa o ano de nascimento e o ano atual. O programa calcula a idade
                    com base na diferença entre esses valores.
                  </p>
                </div>

                <div class="exercise">
                  <div class="tag">EX 005 💸</div>
                  <h4>Desafio da Gorjeta</h4>
                  <p>
                    Calcula o valor da gorjeta com base na porcentagem informada e exibe
                    o total final da conta.
                  </p>
                </div>
              </div>
            </article>

            <article class="block glass reveal" id="como-executar">
              <h3>▶️ Como executar</h3>
              <p>Para rodar o arquivo no seu computador, siga os passos abaixo:</p>
              <pre><code># 1. Salve o código em um arquivo, por exemplo:
exercicios.py

# 2. Execute no terminal:
python exercicios.py

# ou, dependendo do sistema:
python3 exercicios.py</code></pre>
            </article>

            <article class="block glass reveal" id="aprendizados">
              <h3>🎓 Conceitos praticados</h3>
              <ul>
                <li>🔤 Strings e interpolação com <code>f""</code></li>
                <li>⌨️ Entrada de dados com <code>input()</code></li>
                <li>🔢 Conversão de tipos com <code>int()</code> e <code>float()</code></li>
                <li>🧮 Operações aritméticas básicas</li>
                <li>🪄 Organização simples de exercícios em sequência</li>
              </ul>
            </article>

            <article class="block glass reveal" id="codigo">
              <h3>💾 Código-fonte</h3>
              <pre><code>"""
EX 001  Boas-vindas Personalizadas: Crie uma variável para armazenar o nome de
uma pessoa. Peça para o usuário digitar seu nome, armazene-o e depois exiba a
mensagem: "Olá [nome], seja bem-vindo!"
"""
print("===== Boas-vindas Personalizadas: =====\n")
nome = input("Digite o seu nome: ")
print(f"Olá {nome}, seja bem-vindo!\n\n")

"""
EX 002 Endereço Completo: Crie três variáveis: cidade, estado e cep. Peça ao
usuário para preencher cada uma e, ao final, exiba o endereço formatado em
uma única linha.
"""
print("===== Endereço Completo: =====\n")
cidade = input("Digite a sua Cidade: ")
estado = input("Digite o seu Estado: ")
cep = input("Digite o seu Cep: ")
print(f"Você mora em {cidade}, Estado de {estado}, no Cep {cep}\n\n")

"""
EX 003 Soma de Dois Números: Receba dois números inteiros do usuário,
armazeneos em variáveis distintas, calcule a soma e exiba o resultado.
"""
print("===== Soma de Dois Números: =====\n")
n1 = int(input("Digite um valor inteiro: "))
n2 = int(input("Digite outro valor inteiro: "))
print(f"A soma entre {n1} + {n2} = {n1 + n2}\n\n")

"""
EX 004 Calculadora de Idade: Crie uma variável para o ano_nascimento e outra para
o ano_atual. Peça os dados ao usuário, subtraia as variáveis e exiba: "Sua
idade é ou será [resultado] anos".
"""
print("===== Calculadora de Idade: =====\n")
ano_nascimento = int(input("Digite o ano do seu nascimento: "))
ano_atual = int(input("Digite o ano atual: "))
print(f"Sua idade é ou será {ano_atual - ano_nascimento} anos\n\n")

"""
Ex 005 Desafio Calculadora de Gorjeta: * Receba o valor total da conta de um
restaurante. Receba a porcentagem de gorjeta que o cliente deseja deixar (ex:
10, 15 ou 20).
Calcule o valor da gorjeta e o valor total final (conta + gorjeta).
Exiba os dois valores separadamente.
"""
print("===== Desafio Calculadora de Gorjeta: =====\n")
conta = float(input("Digite o valor total da conta: "))
gorjeta = float(input("Digite o percentual que gostaria de ofertar como gorjeta: "))
gorjeta = (gorjeta * conta) / 100
print(f"\nValor final da conta fica em R$:{conta + gorjeta} \nsendo R$:{conta} do consmo no local \ne R$:{gorjeta} de gorjeta ofertada!")</code></pre>
            </article>

            <article class="block glass reveal">
              <h3>📝 Sugestão de README em Markdown</h3>
              <pre><code># 🐍 Exercícios Iniciais em Python

## ✨ Sobre
Este repositório reúne exercícios básicos em Python para praticar:
- 📥 entrada de dados com `input()`
- 🧠 uso de variáveis
- ➕ operações matemáticas
- 🗣️ saída formatada com `f-strings`

## 🧩 Exercícios
### 👋 EX 001 - Boas-vindas Personalizadas
Solicita o nome do usuário e exibe uma mensagem de boas-vindas.

### 📍 EX 002 - Endereço Completo
Recebe cidade, estado e CEP e mostra as informações formatadas.

### ➕ EX 003 - Soma de Dois Números
Lê dois números inteiros, soma e exibe o resultado.

### 🎂 EX 004 - Calculadora de Idade
Calcula a idade com base no ano de nascimento e no ano atual.

### 💸 EX 005 - Calculadora de Gorjeta
Calcula a gorjeta e o valor total final da conta.

## ▶️ Como executar
```bash
python exercicios.py

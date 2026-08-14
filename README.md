Meu Blog Tech
=============
Site estático simples com duas publicações e botões "Curtir" e "Amei". Ideal para enviar como trabalho no Alura.

O que há neste pacote
- index.html — arquivo autossuficiente (HTML + CSS + JS) pronto para abrir no navegador.
- README.md — este arquivo.

Como abrir localmente
1. Salve index.html em uma pasta no seu computador.
2. Abra o arquivo index.html no navegador (duplo clique ou arrastar para uma aba do navegador).

Como editar (rápido)
- Abra index.html em um editor de texto/VS Code.
- Para editar título, posts e conteúdo, edite as seções <article class="post"> no HTML.
- Para alterar contadores iniciais ou comportamento, procure a área de script no final do arquivo e ajuste defaultState.counts.

Resetar contadores/estado (no navegador)
- No Chrome/Firefox: abra DevTools → Aplicação/Storage → Local Storage → remova a chave "meublogtech:singlefile:v1".
- Alternativamente, abra o console do navegador e execute:
  localStorage.removeItem('meublogtech:singlefile:v1');

Compatibilidade
- Funciona em navegadores modernos (Chrome, Firefox, Edge, Safari).
- Armazenamento de likes/amei é local ao navegador (localStorage) e não é global.

Como enviar para o Alura
- Se a atividade pedir um arquivo ZIP: compacte index.html e README.md num ZIP e submeta.
- Se a atividade pedir apenas o arquivo HTML: envie index.html.
- Sugestão de nome do ZIP: MeuBlogTech.zip

Instruções rápidas para criar o ZIP
- Windows PowerShell:
  Compress-Archive -Path .\index.html, .\README.md -DestinationPath .\MeuBlogTech.zip
- macOS / Linux (terminal):
  zip -r MeuBlogTech.zip index.html README.md

Licença
- Use/adapte livremente. Credite se desejar.

<!doctype html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Meu Blog Tech</title>
  <style>
    :root{
      --bg:#071029;
      --card:#0b1220;
      --muted:#9aa6b2;
      --accent:#7c3aed;
      --accent-2:#ef4444;
      --glass: rgba(255,255,255,0.03);
    }
    *{box-sizing:border-box}
    body{
      margin:0;
      font-family: Inter, system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
      background: linear-gradient(180deg,#071029 0%, #071a2a 100%);
      color:#e6eef6;
      -webkit-font-smoothing:antialiased;
      -moz-osx-font-smoothing:grayscale;
      min-height:100vh;
    }
    .container{max-width:900px;margin:2rem auto;padding:0 1rem}
    .site-header{text-align:center;padding:2rem 1rem 1rem}
    .site-header h1{margin:0;font-size:2rem}
    .subtitle{margin:0.25rem 0 0;color:var(--muted)}
    .post{
      background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01));
      border:1px solid rgba(255,255,255,0.03);
      padding:1.25rem;border-radius:12px;margin-bottom:1rem;
      box-shadow: 0 6px 18px rgba(2,6,23,0.6);
    }
    .post h2{margin:0 0 0.25rem}
    .meta{margin:0 0 0.75rem;color:var(--muted);font-size:0.9rem}
    .post-actions{margin-top:1rem;display:flex;gap:0.5rem;align-items:center}
    .btn{
      display:inline-flex;gap:0.5rem;align-items:center;padding:0.5rem 0.75rem;border-radius:10px;
      border:1px solid rgba(255,255,255,0.04);background:var(--glass);color:inherit;cursor:pointer;
      transition:transform .12s ease, box-shadow .12s ease;font-size:0.95rem;
    }
    .btn:active{transform:scale(.98)}
    .btn .icon{width:20px;height:20px;fill:currentColor;opacity:0.95}
    .btn .count{
      background: rgba(255,255,255,0.04);
      padding:0.08rem 0.45rem;border-radius:6px;margin-left:0.25rem;
      color:var(--muted);font-weight:600;font-size:0.9rem;
    }
    .like-btn.active{
      box-shadow:0 6px 18px rgba(124,58,237,0.12);
      color:var(--accent);border-color:rgba(124,58,237,0.25);
    }
    .love-btn.active{
      box-shadow:0 6px 18px rgba(239,68,68,0.12);
      color:var(--accent-2);border-color:rgba(239,68,68,0.25);
    }
    .site-footer{text-align:center;color:var(--muted);padding:2rem 1rem;font-size:0.9rem}
    @media (max-width:600px){
      .container{padding:0 0.75rem}
      .post-actions{flex-wrap:wrap}
    }
  </style>
</head>
<body>
  <header class="site-header">
    <h1>Meu Blog Tech</h1>
    <p class="subtitle">Insights, dicas e reflexões sobre desenvolvimento</p>
  </header>

  <main class="container" id="posts">
    <article class="post" data-post-id="post-1">
      <h2>Como otimizar seu bundle JavaScript</h2>
      <p class="meta">13 de agosto de 2026 • Por Lucas</p>
      <p>Este post mostra técnicas práticas para reduzir o tamanho do bundle: code-splitting, tree-shaking, lazy loading e compressão.</p>

      <div class="post-actions">
        <button class="btn like-btn" aria-pressed="false" aria-label="Curtir esta publicação">
          <svg class="icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M12 21s-7-4.35-9-7.17C1.9 11.8 3.6 7 7.5 7c1.9 0 3.1 1.1 4.5 3.1C13.4 8.1 14.6 7 16.5 7 20.4 7 22.1 11.8 21 13.83 19 16.65 12 21 12 21z"/></svg>
          <span class="label">Curtir</span>
          <span class="count">0</span>
        </button>

        <button class="btn love-btn" aria-pressed="false" aria-label="Amei esta publicação">
          <svg class="icon" viewBox="0 0 24 24" aria-hidden="true"><path d="M12 21s-1-.7-2.5-1.9C6 16 3 13.4 3 9.8 3 6.6 5.6 4 8.8 4c1.9 0 3.1 1.1 4.5 3.1C14.1 5.1 15.3 4 17.2 4 20.4 4 23 6.6 23 9.8c0 3.6-3
# VoudeBarato
Plataforma de comparação de tarifas de ônibus e avião, com foco em economia, praticidade e experiência do usuário.
<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>VOU DE BARATO — Menor Tarifa em Tempo Real</title>
<meta name="description" content="Compare passagens de ônibus e avião para encontrar a menor tarifa.">
<style>
:root{
  --preto:#090909;
  --preto2:#111111;
  --cinza:#1b1b1b;
  --cinza2:#252525;
  --texto:#f5f5f5;
  --texto2:#bdbdbd;
  --laranja:#ff7a00;
  --laranja2:#ff9a2f;
  --borda:rgba(255,122,0,.22);
  --verde:#31c878;
}
*{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{
  font-family:Arial,Helvetica,sans-serif;
  background:var(--preto);
  color:var(--texto);
  line-height:1.5;
}
button,input{font:inherit}
button{cursor:pointer}
a{color:inherit;text-decoration:none}
.container{width:min(1180px,92%);margin:auto}
header{
  position:sticky;top:0;z-index:1000;
  background:rgba(9,9,9,.95);
  backdrop-filter:blur(12px);
  border-bottom:1px solid #222;
}
.nav{
  min-height:78px;display:flex;align-items:center;gap:30px;
}
.logo-link{display:flex;align-items:center;flex-shrink:0}
.logo{width:190px;height:auto;display:block}.logo-fallback{min-width:190px}
.menu{display:flex;align-items:center;gap:8px;margin-left:auto}
.menu button{
  border:0;background:transparent;color:#ddd;padding:11px 13px;border-radius:9px;
  transition:.2s;font-weight:700;font-size:14px;
}
.menu button:hover,.menu button.ativo{color:#fff;background:#1b1b1b}
.menu .login{border:1px solid var(--laranja);color:var(--laranja)}
.menu .login:hover{background:var(--laranja);color:#111}
.mobile-menu{display:none;background:#1a1a1a;border:1px solid #333;color:white;border-radius:8px;padding:9px 12px}

.page-section{display:none}
.page-section.ativo{display:block}
#inicio.page-section{display:block}

.hero{
  min-height:590px;display:flex;align-items:center;
  position:relative;overflow:hidden;
  background:
    radial-gradient(circle at 80% 25%,rgba(255,122,0,.16),transparent 28%),
    linear-gradient(120deg,#090909 0%,#111 55%,#0a0a0a 100%);
}
.hero:after{
  content:"";position:absolute;width:430px;height:430px;border-radius:50%;
  right:-130px;bottom:-210px;border:1px solid rgba(255,122,0,.13);
  box-shadow:0 0 100px rgba(255,122,0,.08);
}
.hero-content{position:relative;z-index:2;padding:70px 0}
.tag{
  display:inline-block;color:var(--laranja);font-weight:800;letter-spacing:2px;
  font-size:13px;margin-bottom:16px;
}
h1{font-size:clamp(38px,6vw,70px);line-height:1.02;max-width:700px}
h1 span{color:var(--laranja)}
.hero p{color:#c7c7c7;max-width:680px;font-size:18px;margin:22px 0 28px}
.decor{position:absolute;right:7%;top:21%;font-size:90px;opacity:.15;filter:drop-shadow(0 0 25px var(--laranja))}
.decor .bus{font-size:70px;margin-left:100px}

.search-box{
  background:rgba(20,20,20,.96);border:1px solid var(--borda);
  border-radius:18px;padding:20px;box-shadow:0 20px 70px rgba(0,0,0,.4);
}
.tipo{display:flex;gap:8px;margin-bottom:17px}
.tipo button{
  background:#191919;border:1px solid #333;color:#ddd;border-radius:9px;padding:9px 15px;font-weight:700
}
.tipo button.ativo{background:var(--laranja);border-color:var(--laranja);color:#111}
.form-grid{display:grid;grid-template-columns:1.25fr 1.25fr 1fr 1fr .75fr;gap:10px}
.campo{position:relative}
.campo label{display:block;color:#aaa;font-size:12px;font-weight:700;margin:0 0 6px 3px}
.campo input,.campo select{
  width:100%;height:48px;background:#0d0d0d;border:1px solid #3a3a3a;
  border-radius:9px;color:white;padding:0 12px;outline:none;
}
.campo input:focus,.campo select:focus{border-color:var(--laranja)}
.autocomplete{
  display:none;position:absolute;top:76px;left:0;right:0;background:#171717;
  border:1px solid #444;border-radius:10px;z-index:50;overflow:hidden;box-shadow:0 15px 40px #000;
}
.autocomplete.ativo{display:block}
.sugestao{padding:11px 13px;border-bottom:1px solid #292929;cursor:pointer}
.sugestao:hover{background:#242424}
.sugestao strong{display:block}
.sugestao small{color:#999}
.btn-buscar{
  width:100%;height:48px;margin-top:21px;border:0;border-radius:10px;
  background:var(--laranja);color:#111;font-weight:900;
  transition:.2s;
}
.btn-buscar:hover{background:var(--laranja2);transform:translateY(-1px)}
.trust{display:grid;grid-template-columns:repeat(3,1fr);gap:15px;margin-top:18px}
.trust div{background:#101010;border:1px solid #222;border-radius:10px;padding:13px;text-align:center;color:#bbb;font-size:13px}

.content{padding:70px 0}
.section-title{text-align:center;margin-bottom:35px}
.section-title h2{font-size:38px}
.section-title p{color:#aaa;margin-top:8px}
.cards3{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.info-card,.result-card,.faq,.login-box,.promo-card{
  background:#141414;border:1px solid #2b2b2b;border-radius:15px;
}
.info-card{padding:25px}
.icon{font-size:30px;margin-bottom:10px}
.info-card h3{margin-bottom:7px}
.info-card p{color:#aaa}

#resultados{padding:70px 0}
.result-head{display:flex;justify-content:space-between;align-items:end;gap:20px;margin-bottom:20px}
.result-head h2{font-size:32px}
.result-route{color:#aaa}
.summary{display:grid;grid-template-columns:repeat(3,1fr);gap:15px}
.summary-card{padding:20px;border-radius:14px;background:#151515;border:1px solid #333}
.summary-card.destaque{border-color:var(--laranja)}
.summary-card .small{color:#aaa;font-size:13px}
.summary-card .price{font-size:30px;font-weight:900;margin:4px 0}
.summary-card .desc{color:#ccc;font-size:14px}
.economia{
  margin:18px 0;padding:18px 20px;border-radius:12px;
  background:rgba(49,200,120,.08);border:1px solid rgba(49,200,120,.35);color:#c8f4dd
}
.results-list{display:grid;gap:13px;margin-top:20px}
.result-card{padding:20px}
.result-top{display:flex;justify-content:space-between;gap:20px}
.empresa{font-weight:900;font-size:18px}
.tipo-resultado{color:var(--laranja);font-size:13px;font-weight:700;margin-top:3px}
.badge{display:inline-block;background:#242424;color:#ddd;border-radius:20px;padding:5px 9px;font-size:11px;margin:5px 5px 0 0}
.result-grid{display:grid;grid-template-columns:1.4fr .8fr .8fr .8fr;gap:15px;align-items:center;margin-top:17px}
.valor{font-size:27px;font-weight:900}
.antigo{text-decoration:line-through;color:#777;font-size:12px}
.result-info{color:#bbb;font-size:13px}
.result-action{text-align:right}
.btn-oficial{
  background:transparent;border:1px solid var(--laranja);color:var(--laranja);
  border-radius:8px;padding:10px 13px;font-weight:800;
}
.btn-oficial:hover{background:var(--laranja);color:#111}
.sem-resultados{
  text-align:center;padding:35px;border:1px dashed #444;border-radius:14px;color:#aaa
}
.btn-voltar{
  border:1px solid #444;background:#181818;color:#eee;padding:10px 15px;border-radius:9px;font-weight:700
}
.btn-voltar:hover{border-color:var(--laranja);color:var(--laranja)}

.promo-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:18px}
.promo-card{padding:24px;position:relative;overflow:hidden}
.promo-card:before{content:"";position:absolute;right:-35px;top:-35px;width:100px;height:100px;border-radius:50%;background:rgba(255,122,0,.12)}
.promo-tag{color:var(--laranja);font-weight:900;font-size:12px;letter-spacing:1px}
.promo-card h3{font-size:22px;margin:9px 0}
.promo-card p{color:#aaa}
.promo-card .promo-price{font-size:28px;font-weight:900;margin-top:15px}

.steps{display:grid;grid-template-columns:repeat(4,1fr);gap:18px}
.step{padding:24px;background:#141414;border:1px solid #292929;border-radius:15px}
.num{width:36px;height:36px;border-radius:50%;display:grid;place-items:center;background:var(--laranja);color:#111;font-weight:900;margin-bottom:13px}

.help-grid{display:grid;grid-template-columns:1.5fr 1fr;gap:22px}
.faq{padding:19px;margin-bottom:10px}
.faq summary{cursor:pointer;font-weight:800}
.faq p{color:#aaa;margin-top:12px}
.contact-box{background:#141414;border:1px solid #2b2b2b;border-radius:15px;padding:25px;height:max-content}
.contact-box p{color:#aaa;margin:9px 0 20px}

.login-wrap{display:grid;place-items:center;min-height:520px}
.login-box{width:min(430px,100%);padding:30px}
.login-box h2{font-size:30px}
.login-box p{color:#999;margin:7px 0 22px}
.login-box input{width:100%;height:48px;background:#0c0c0c;color:white;border:1px solid #3a3a3a;border-radius:9px;padding:0 12px;margin-bottom:12px}
.login-box .btn-buscar{margin-top:3px}
.login-link{background:none;border:0;color:var(--laranja);font-weight:700;margin-top:15px}

footer{border-top:1px solid #222;padding:35px 0;color:#888}
.footer-grid{display:flex;justify-content:space-between;gap:20px;flex-wrap:wrap}
.footer-links{display:flex;gap:18px;flex-wrap:wrap}
.footer-links button{background:none;border:0;color:#aaa;cursor:pointer}
.footer-links button:hover{color:var(--laranja)}

.toast{
  position:fixed;right:20px;bottom:20px;z-index:2000;display:none;
  background:#171717;border:1px solid var(--laranja);color:#fff;border-radius:10px;padding:14px 17px;
  box-shadow:0 10px 35px #000;max-width:380px;
}
.toast.ativo{display:block}

@media(max-width:900px){
  .menu{display:none}
  .mobile-menu{display:block;margin-left:auto}
  .menu.mobile-open{display:flex;position:absolute;top:78px;left:0;right:0;background:#111;padding:12px;flex-direction:column;align-items:stretch;border-bottom:1px solid #333}
  .form-grid{grid-template-columns:1fr 1fr}
  .cards3,.summary,.promo-grid,.steps{grid-template-columns:1fr}
  .result-grid{grid-template-columns:1fr 1fr}
  .result-action{text-align:left}
  .help-grid{grid-template-columns:1fr}
}
@media(max-width:600px){
  .logo{width:155px}
  .hero{min-height:auto}
  .hero-content{padding:55px 0}
  .hero p{font-size:16px}
  .decor{display:none}
  .form-grid{grid-template-columns:1fr}
  .trust{grid-template-columns:1fr}
  .result-head{align-items:start;flex-direction:column}
  .result-grid{grid-template-columns:1fr}
}
</style>
</head>

<body>

<header>
  <div class="container nav">
    <a href="#inicio" class="logo-link" onclick="mostrarPagina('inicio');">
      <img
        src="./logo-site.png"
        alt="VOU DE BARATO"
        class="logo"
        id="logoPrincipal"
        onerror="tentarLogoAlternativa(this)"
      >
    </a>

    <button class="mobile-menu" onclick="toggleMenu()" aria-label="Abrir menu">☰</button>

    <nav class="menu" id="menu">
      <button data-page="inicio" class="ativo" onclick="mostrarPagina('inicio')">INÍCIO</button>
      <button data-page="promocoes" onclick="mostrarPagina('promocoes')">PROMOÇÕES</button>
      <button data-page="como-funciona" onclick="mostrarPagina('como-funciona')">COMO FUNCIONA</button>
      <button data-page="ajuda" onclick="mostrarPagina('ajuda')">AJUDA</button>
      <button data-page="entrar" class="login" onclick="mostrarPagina('entrar')">ENTRAR</button>
    </nav>
  </div>
</header>

<main>

<section id="inicio" class="page-section ativo">
  <div class="hero">
    <div class="container hero-content">
      <div class="tag">MENOR TARIFA EM TEMPO REAL</div>
      <h1>VIAJE <span>PAGANDO MENOS.</span></h1>
      <p>Compare passagens de ônibus e avião em tempo real para encontrar a menor tarifa para a sua viagem.</p>

      <div class="search-box">
        <div class="tipo">
          <button id="tipo-todos" class="ativo" onclick="tipoTransporte('todos',this)">🔎 Todos</button>
          <button onclick="tipoTransporte('onibus',this)">🚌 Ônibus</button>
          <button onclick="tipoTransporte('aviao',this)">✈️ Avião</button>
        </div>

        <div class="form-grid">
          <div class="campo">
            <label>De onde você vai sair?</label>
            <input id="origem" type="text" placeholder="Ex.: São Paulo" autocomplete="off">
            <div id="sugestoes-origem" class="autocomplete"></div>
          </div>

          <div class="campo">
            <label>Para onde você quer viajar?</label>
            <input id="destino" type="text" placeholder="Ex.: Salvador" autocomplete="off">
            <div id="sugestoes-destino" class="autocomplete"></div>
          </div>

          <div class="campo">
            <label>Data da ida</label>
            <input id="ida" type="date">
          </div>

          <div class="campo">
            <label>Data da volta (opcional)</label>
            <input id="volta" type="date">
          </div>

          <div class="campo">
            <label>Passageiros</label>
            <select id="passageiros">
              <option>1 passageiro</option>
              <option>2 passageiros</option>
              <option>3 passageiros</option>
              <option>4 passageiros</option>
              <option>5+ passageiros</option>
            </select>
          </div>
        </div>

        <button class="btn-buscar" onclick="buscar()">🔍 BUSCAR MENOR TARIFA</button>
      </div>

      <div class="trust">
        <div>💰 Compare preços</div>
        <div>⚡ Veja as opções rapidamente</div>
        <div>🔒 Compra no site oficial</div>
      </div>
    </div>
    <div class="decor">✈️<div class="bus">🚌</div></div>
  </div>
</section>

<section id="resultados" class="page-section">
  <div class="container">
    <div class="result-head">
      <div>
        <button class="btn-voltar" onclick="mostrarPagina('inicio')">← VOLTAR PARA O INÍCIO</button>
        <h2 id="titulo-resultados" style="margin-top:18px">Resultados</h2>
        <div class="result-route" id="rota-resultados"></div>
      </div>
    </div>

    <div id="carregando" class="sem-resultados" style="display:none">
      🔍 Estamos comparando tarifas disponíveis...
    </div>

    <div id="conteudo-resultados">
      <div class="summary">
        <div class="summary-card destaque">
          <div class="small">🏆 MENOR PREÇO</div>
          <div class="price" id="menor-preco">—</div>
          <div class="desc" id="menor-preco-desc">—</div>
        </div>
        <div class="summary-card">
          <div class="small">⚡ MAIS RÁPIDO</div>
          <div class="price" id="mais-rapido">—</div>
          <div class="desc" id="mais-rapido-desc">—</div>
        </div>
        <div class="summary-card">
          <div class="small">⭐ CUSTO-BENEFÍCIO</div>
          <div class="price" id="custo-beneficio">—</div>
          <div class="desc" id="custo-beneficio-desc">—</div>
        </div>
      </div>

      <div class="economia" id="economia">💰 Compare as opções abaixo para descobrir quanto você pode economizar.</div>
      <div class="demo-note" style="margin:16px 0;padding:12px 15px;border:1px solid rgba(255,122,0,.2);border-radius:12px;background:#121212;color:#bdbdbd;font-size:13px;">⚠️ <strong style="color:#fff">Modo demonstração:</strong> os preços e horários são exemplos. A regra de rota já está preparada: só aparecem empresas cadastradas para a origem e o destino escolhidos. A disponibilidade e as tarifas reais serão conectadas posteriormente.</div>
      <div id="lista-resultados" class="results-list"></div>
    </div>
  </div>
</section>

<section id="promocoes" class="page-section content">
  <div class="container">
    <div class="section-title">
      <h2>🔥 Promoções</h2>
      <p>Ofertas em destaque para quem quer viajar pagando menos.</p>
    </div>
    <div class="promo-grid">
      <article class="promo-card">
        <div class="promo-tag">ÔNIBUS</div>
        <h3>Ofertas de passagens rodoviárias</h3>
        <p>Encontre tarifas promocionais de diferentes empresas e compare antes de comprar.</p>
        <div class="promo-price">A partir de R$ 49,90</div>
      </article>
      <article class="promo-card">
        <div class="promo-tag">AVIÃO</div>
        <h3>Tarifas aéreas em destaque</h3>
        <p>Compare opções aéreas e acompanhe oportunidades de preços mais baixos.</p>
        <div class="promo-price">A partir de R$ 199,90</div>
      </article>
      <article class="promo-card">
        <div class="promo-tag">DICA</div>
        <h3>Compare antes de comprar</h3>
        <p>O mesmo destino pode ter preços e tempos de viagem muito diferentes.</p>
        <div class="promo-price">Economize mais</div>
      </article>
    </div>
  </div>
</section>

<section id="como-funciona" class="page-section content">
  <div class="container">
    <div class="section-title">
      <h2>Como funciona</h2>
      <p>Encontrar uma passagem mais barata pode ser simples.</p>
    </div>
    <div class="steps">
      <div class="step"><div class="num">1</div><h3>Informe sua viagem</h3><p>Escolha origem, destino, datas e número de passageiros.</p></div>
      <div class="step"><div class="num">2</div><h3>Compare</h3><p>Veja as opções disponíveis de ônibus e avião em uma única tela.</p></div>
      <div class="step"><div class="num">3</div><h3>Encontre a melhor opção</h3><p>Confira preço, duração, tipo de serviço e economia.</p></div>
      <div class="step"><div class="num">4</div><h3>Compre no oficial</h3><p>Você é direcionado para o site oficial da empresa para finalizar a compra.</p></div>
    </div>
  </div>
</section>

<section id="ajuda" class="page-section content">
  <div class="container">
    <div class="section-title">
      <h2>Ajuda</h2>
      <p>Respostas rápidas para as principais dúvidas.</p>
    </div>

    <div class="help-grid">
      <div>
        <details class="faq">
          <summary>O VOU DE BARATO vende as passagens?</summary>
          <p>Não. A proposta é comparar opções e direcionar você para o site oficial da empresa escolhida.</p>
        </details>
        <details class="faq">
          <summary>Os preços mostrados são definitivos?</summary>
          <p>Os valores podem mudar. Antes da compra, confira o preço final no site oficial da empresa.</p>
        </details>
        <details class="faq">
          <summary>Posso comparar ônibus e avião?</summary>
          <p>Sim. Use a opção “Todos” para visualizar os dois tipos de transporte quando houver dados disponíveis para a rota.</p>
        </details>
        <details class="faq">
          <summary>Por que uma empresa não aparece na minha rota?</summary>
          <p>Uma empresa só deve aparecer quando houver uma opção cadastrada para a origem e o destino pesquisados. Na versão real, essa informação será alimentada por fontes de tarifas e disponibilidade.</p>
        </details>
      </div>

      <div class="contact-box">
        <h3>Não encontrou sua resposta?</h3>
        <p>Em uma próxima etapa, podemos conectar esta área a um formulário de atendimento ou canal de contato.</p>
        <button class="btn-oficial" onclick="mostrarAviso('Canal de contato em desenvolvimento.')">FALE CONOSCO</button>
      </div>
    </div>
  </div>
</section>

<section id="entrar" class="page-section content">
  <div class="container login-wrap">
    <div class="login-box">
      <h2>Entrar</h2>
      <p>Acesse sua conta para salvar viagens e acompanhar suas preferências.</p>
      <input id="email" type="email" placeholder="Seu e-mail">
      <input id="senha" type="password" placeholder="Sua senha">
      <button class="btn-buscar" onclick="entrar()">ENTRAR</button>
      <button class="login-link" onclick="mostrarAviso('Cadastro de usuário em desenvolvimento.')">Ainda não tenho conta</button>
    </div>
  </div>
</section>

</main>

<footer>
  <div class="container footer-grid">
    <div>© 2026 VOU DE BARATO — Menor Tarifa em Tempo Real</div>
    <div class="footer-links">
      <button onclick="mostrarPagina('inicio')">Início</button>
      <button onclick="mostrarPagina('promocoes')">Promoções</button>
      <button onclick="mostrarPagina('como-funciona')">Como funciona</button>
      <button onclick="mostrarPagina('ajuda')">Ajuda</button>
      <button onclick="mostrarAviso('Política de Privacidade em desenvolvimento.')">Privacidade</button>
    </div>
  </div>
</footer>

<div id="toast" class="toast"></div>

<script>
/* =========================================================
   VOU DE BARATO — lógica da versão de demonstração
   ========================================================= */

const cidades = [
  {nome:"São Paulo", uf:"SP"},
  {nome:"Rio de Janeiro", uf:"RJ"},
  {nome:"Salvador", uf:"BA"},
  {nome:"Curitiba", uf:"PR"},
  {nome:"Belo Horizonte", uf:"MG"},
  {nome:"Brasília", uf:"DF"},
  {nome:"Porto Alegre", uf:"RS"},
  {nome:"Florianópolis", uf:"SC"},
  {nome:"Foz do Iguaçu", uf:"PR"},
  {nome:"Recife", uf:"PE"},
  {nome:"Fortaleza", uf:"CE"},
  {nome:"Goiânia", uf:"GO"},
  {nome:"Campinas", uf:"SP"},
  {nome:"Santos", uf:"SP"},
  {nome:"Niterói", uf:"RJ"}
];

let transporteSelecionado = "todos";

/*
  DADOS DE DEMONSTRAÇÃO POR ROTA.
  REGRA FUNDAMENTAL: uma empresa só aparece se existir um
  registro explícito para a origem + destino + tipo pesquisados.
  Não existe uma lista global de empresas que seja exibida para
  qualquer cidade. Assim, São Paulo → Brasília, por exemplo,
  possui somente os operadores cadastrados para esse trecho.
  A mesma regra vale para todas as demais rotas.
*/
const ofertas = [
  // SÃO PAULO → SALVADOR
  {origem:"São Paulo",destino:"Salvador",tipo:"onibus",empresa:"ClickBus",preco:139.90,horario:"18:30",duracao:1500,servico:"Convencional",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.clickbus.com.br/"},
  {origem:"São Paulo",destino:"Salvador",tipo:"onibus",empresa:"Gontijo",preco:159.90,horario:"19:10",duracao:1440,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.gontijo.com.br/"},
  {origem:"São Paulo",destino:"Salvador",tipo:"onibus",empresa:"Águia Branca",preco:174.90,horario:"20:00",duracao:1380,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,6",oficial:"https://www.aguiabranca.com.br/"},
  {origem:"São Paulo",destino:"Salvador",tipo:"aviao",empresa:"GOL",preco:279.00,horario:"07:15",duracao:145,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.voegol.com.br/"},
  {origem:"São Paulo",destino:"Salvador",tipo:"aviao",empresa:"LATAM",preco:319.90,horario:"10:20",duracao:140,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"São Paulo",destino:"Salvador",tipo:"aviao",empresa:"Azul",preco:329.90,horario:"14:10",duracao:145,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.voeazul.com.br/"},

  // SÃO PAULO → BRASÍLIA
  // Operadores de ônibus confirmados em fonte de consulta de rota; valores/horários abaixo são apenas demonstrativos.
  {origem:"São Paulo",destino:"Brasília",tipo:"onibus",empresa:"ClickBus",preco:189.00,horario:"10:00",duracao:1065,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.clickbus.com.br/"},
  {origem:"São Paulo",destino:"Brasília",tipo:"onibus",empresa:"Real Expresso",preco:219.90,horario:"10:00",duracao:1065,servico:"Leito",bagagem:"1 bagagem",avaliacao:"4,6",oficial:"https://www.realexpresso.com.br/"},
  {origem:"São Paulo",destino:"Brasília",tipo:"onibus",empresa:"Catedral",preco:209.90,horario:"12:30",duracao:1080,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.catedralbus.com.br/"},
  {origem:"São Paulo",destino:"Brasília",tipo:"onibus",empresa:"Rápido Federal",preco:229.90,horario:"18:30",duracao:1080,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.clickbus.com.br/"},
  {origem:"São Paulo",destino:"Brasília",tipo:"aviao",empresa:"GOL",preco:394.65,horario:"07:15",duracao:105,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.voegol.com.br/"},
  {origem:"São Paulo",destino:"Brasília",tipo:"aviao",empresa:"LATAM",preco:432.65,horario:"09:20",duracao:105,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"São Paulo",destino:"Brasília",tipo:"aviao",empresa:"Azul",preco:417.04,horario:"14:10",duracao:110,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.voeazul.com.br/"},

  // BRASÍLIA → SÃO PAULO
  {origem:"Brasília",destino:"São Paulo",tipo:"onibus",empresa:"ClickBus",preco:189.00,horario:"08:00",duracao:1065,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.clickbus.com.br/"},
  {origem:"Brasília",destino:"São Paulo",tipo:"onibus",empresa:"Real Expresso",preco:219.90,horario:"10:00",duracao:1065,servico:"Leito",bagagem:"1 bagagem",avaliacao:"4,6",oficial:"https://www.realexpresso.com.br/"},
  {origem:"Brasília",destino:"São Paulo",tipo:"onibus",empresa:"Catedral",preco:209.90,horario:"12:30",duracao:1080,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.catedralbus.com.br/"},
  {origem:"Brasília",destino:"São Paulo",tipo:"onibus",empresa:"Rápido Federal",preco:229.90,horario:"18:30",duracao:1080,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.clickbus.com.br/"},
  {origem:"Brasília",destino:"São Paulo",tipo:"aviao",empresa:"GOL",preco:394.65,horario:"07:15",duracao:105,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.voegol.com.br/"},
  {origem:"Brasília",destino:"São Paulo",tipo:"aviao",empresa:"LATAM",preco:432.65,horario:"09:20",duracao:105,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"Brasília",destino:"São Paulo",tipo:"aviao",empresa:"Azul",preco:417.04,horario:"14:10",duracao:110,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.voeazul.com.br/"},

  // SÃO PAULO → RIO DE JANEIRO
  {origem:"São Paulo",destino:"Rio de Janeiro",tipo:"onibus",empresa:"ClickBus",preco:69.90,horario:"06:30",duracao:390,servico:"Convencional",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.clickbus.com.br/"},
  {origem:"São Paulo",destino:"Rio de Janeiro",tipo:"onibus",empresa:"Viação Cometa",preco:79.90,horario:"08:00",duracao:390,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,6",oficial:"https://www.viacaocometa.com.br/"},
  {origem:"São Paulo",destino:"Rio de Janeiro",tipo:"onibus",empresa:"1001",preco:89.90,horario:"09:30",duracao:380,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.autoviacao1001.com.br/"},
  {origem:"São Paulo",destino:"Rio de Janeiro",tipo:"aviao",empresa:"GOL",preco:219.90,horario:"09:10",duracao:65,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.voegol.com.br/"},
  {origem:"São Paulo",destino:"Rio de Janeiro",tipo:"aviao",empresa:"LATAM",preco:229.90,horario:"12:30",duracao:65,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"São Paulo",destino:"Rio de Janeiro",tipo:"aviao",empresa:"Azul",preco:239.90,horario:"16:40",duracao:65,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.voeazul.com.br/"},

  // RIO DE JANEIRO → SÃO PAULO
  {origem:"Rio de Janeiro",destino:"São Paulo",tipo:"onibus",empresa:"ClickBus",preco:64.90,horario:"07:00",duracao:380,servico:"Convencional",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.clickbus.com.br/"},
  {origem:"Rio de Janeiro",destino:"São Paulo",tipo:"onibus",empresa:"1001",preco:74.90,horario:"08:00",duracao:370,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.autoviacao1001.com.br/"},
  {origem:"Rio de Janeiro",destino:"São Paulo",tipo:"onibus",empresa:"Viação Cometa",preco:79.90,horario:"10:00",duracao:380,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,6",oficial:"https://www.viacaocometa.com.br/"},
  {origem:"Rio de Janeiro",destino:"São Paulo",tipo:"aviao",empresa:"GOL",preco:199.90,horario:"11:20",duracao:65,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.voegol.com.br/"},
  {origem:"Rio de Janeiro",destino:"São Paulo",tipo:"aviao",empresa:"LATAM",preco:209.90,horario:"13:10",duracao:65,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,7",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"Rio de Janeiro",destino:"São Paulo",tipo:"aviao",empresa:"Azul",preco:229.90,horario:"17:30",duracao:65,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.voeazul.com.br/"},

  // CURITIBA → SÃO PAULO
  {origem:"Curitiba",destino:"São Paulo",tipo:"onibus",empresa:"ClickBus",preco:69.90,horario:"07:00",duracao:390,servico:"Convencional",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.clickbus.com.br/"},
  {origem:"Curitiba",destino:"São Paulo",tipo:"onibus",empresa:"Viação Catarinense",preco:79.90,horario:"08:30",duracao:390,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.catarinense.com.br/"},
  {origem:"Curitiba",destino:"São Paulo",tipo:"onibus",empresa:"Expresso Princesa dos Campos",preco:84.90,horario:"10:00",duracao:400,servico:"Executivo",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.princesadoscampos.com.br/"},
  {origem:"Curitiba",destino:"São Paulo",tipo:"aviao",empresa:"GOL",preco:189.90,horario:"13:30",duracao:60,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,5",oficial:"https://www.voegol.com.br/"},
  {origem:"Curitiba",destino:"São Paulo",tipo:"aviao",empresa:"LATAM",preco:199.90,horario:"15:20",duracao:60,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"Curitiba",destino:"São Paulo",tipo:"aviao",empresa:"Azul",preco:209.90,horario:"18:00",duracao:60,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,5",oficial:"https://www.voeazul.com.br/"},

  // FOZ DO IGUAÇU → SÃO PAULO
  {origem:"Foz do Iguaçu",destino:"São Paulo",tipo:"onibus",empresa:"ClickBus",preco:159.90,horario:"18:00",duracao:1060,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.clickbus.com.br/"},
  {origem:"Foz do Iguaçu",destino:"São Paulo",tipo:"aviao",empresa:"GOL",preco:319.90,horario:"14:20",duracao:105,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,5",oficial:"https://www.voegol.com.br/"},
  {origem:"Foz do Iguaçu",destino:"São Paulo",tipo:"aviao",empresa:"LATAM",preco:349.90,horario:"16:10",duracao:105,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,6",oficial:"https://www.latamairlines.com/br/pt"},
  {origem:"Foz do Iguaçu",destino:"São Paulo",tipo:"aviao",empresa:"Azul",preco:359.90,horario:"19:30",duracao:110,servico:"Econômica",bagagem:"Bagagem de mão",avaliacao:"4,5",oficial:"https://www.voeazul.com.br/"},

  // FOZ DO IGUAÇU → CURITIBA
  {origem:"Foz do Iguaçu",destino:"Curitiba",tipo:"onibus",empresa:"ClickBus",preco:119.90,horario:"09:00",duracao:600,servico:"Leito",bagagem:"1 bagagem",avaliacao:"4,4",oficial:"https://www.clickbus.com.br/"},
  {origem:"Foz do Iguaçu",destino:"Curitiba",tipo:"onibus",empresa:"Viação Catarinense",preco:129.90,horario:"10:30",duracao:570,servico:"Semi-leito",bagagem:"1 bagagem",avaliacao:"4,5",oficial:"https://www.catarinense.com.br/"}
];

function chaveRota(origem, destino){
  return `${normalizar(origem)}|${normalizar(destino)}`;
}

function rotasDisponiveis(origem, destino){
  return [...new Set(
    ofertas
      .filter(o => normalizar(o.origem) === normalizar(origem) && normalizar(o.destino) === normalizar(destino))
      .map(o => `${o.tipo}|${o.empresa}`)
  )];
}

function normalizar(texto){
  return (texto || "")
    .normalize("NFD")
    .replace(/[\u0300-\u036f]/g,"")
    .trim()
    .toLowerCase();
}

function cidadeOficial(valor){
  const n = normalizar(valor);
  return cidades.find(c => normalizar(c.nome) === n)?.nome || valor.trim();
}

function formatarMoeda(v){
  return v.toLocaleString("pt-BR",{style:"currency",currency:"BRL"});
}

function formatarDuracao(min){
  const h = Math.floor(min/60);
  const m = min%60;
  return `${h}h${String(m).padStart(2,"0")}`;
}

function mostrarAviso(msg){
  const toast = document.getElementById("toast");
  toast.textContent = msg;
  toast.classList.add("ativo");
  clearTimeout(window.toastTimer);
  window.toastTimer = setTimeout(()=>toast.classList.remove("ativo"),3500);
}

function fecharMenu(){
  document.getElementById("menu").classList.remove("mobile-open");
}

function toggleMenu(){
  document.getElementById("menu").classList.toggle("mobile-open");
}

function mostrarPagina(id){
  document.querySelectorAll(".page-section").forEach(s=>s.classList.remove("ativo"));
  const pagina = document.getElementById(id);
  if(pagina) pagina.classList.add("ativo");

  document.querySelectorAll(".menu button[data-page]").forEach(b=>{
    b.classList.toggle("ativo", b.dataset.page === id);
  });

  fecharMenu();
  window.scrollTo({top:0,behavior:"smooth"});
}

/* O botão da logo volta para o início de verdade. */
document.querySelector(".logo-link").addEventListener("click", function(e){
  e.preventDefault();
  mostrarPagina("inicio");
});

function tipoTransporte(tipo, botao){
  transporteSelecionado = tipo;
  document.querySelectorAll(".tipo button").forEach(b=>b.classList.remove("ativo"));
  botao.classList.add("ativo");
}

/* Logo: tenta os nomes que já foram usados durante o desenvolvimento. */
function tentarLogoAlternativa(img){
  const alternativas = ["./logo-site.png.png","./logo.png","./logo-site.jpg","./logo.jpg"];
  const atual = img.dataset.tentativas ? Number(img.dataset.tentativas) : 0;

  if(atual < alternativas.length){
    img.dataset.tentativas = atual + 1;
    img.src = alternativas[atual];
    return;
  }

  /* Se nenhum arquivo existir, mantém uma identificação visual da marca
     em vez de deixar o espaço do logo quebrado. */
  img.style.display = "none";
  const link = img.closest(".logo-link");
  link.classList.add("logo-fallback");
  link.innerHTML = '<span style="font-size:22px;font-weight:900;letter-spacing:1px;color:#fff">VOU DE <span style="color:#ff7a00">BARATO</span></span>';
}

/* Autocomplete de cidades */
function configurarAutocomplete(inputId, listaId){
  const input = document.getElementById(inputId);
  const lista = document.getElementById(listaId);

  input.addEventListener("input",()=>{
    const termo = normalizar(input.value);
    lista.innerHTML = "";

    if(!termo){
      lista.classList.remove("ativo");
      return;
    }

    const resultados = cidades
      .filter(c => normalizar(c.nome).includes(termo) || normalizar(c.uf).includes(termo))
      .slice(0,6);

    if(!resultados.length){
      lista.classList.remove("ativo");
      return;
    }

    resultados.forEach(c=>{
      const div = document.createElement("div");
      div.className = "sugestao";
      div.innerHTML = `<strong>${c.nome}</strong><small>${c.uf}</small>`;
      div.addEventListener("click",()=>{
        input.value = c.nome;
        lista.classList.remove("ativo");
      });
      lista.appendChild(div);
    });

    lista.classList.add("ativo");
  });

  input.addEventListener("blur",()=>{
    setTimeout(()=>lista.classList.remove("ativo"),180);
  });
}

configurarAutocomplete("origem","sugestoes-origem");
configurarAutocomplete("destino","sugestoes-destino");

/* Busca */
function buscar(){
  const origemInput = document.getElementById("origem").value;
  const destinoInput = document.getElementById("destino").value;

  if(!origemInput || !destinoInput){
    mostrarAviso("Informe a origem e o destino para fazer a busca.");
    return;
  }

  const origem = cidadeOficial(origemInput);
  const destino = cidadeOficial(destinoInput);

  if(normalizar(origem) === normalizar(destino)){
    mostrarAviso("A origem e o destino precisam ser diferentes.");
    return;
  }

  const dataIda = document.getElementById("ida").value;
  if(!dataIda){
    mostrarAviso("Escolha a data da ida.");
    return;
  }

  mostrarPagina("resultados");

  document.getElementById("titulo-resultados").textContent = `Menores tarifas`;
  document.getElementById("rota-resultados").textContent = `${origem} → ${destino}`;

  const carregando = document.getElementById("carregando");
  const conteudo = document.getElementById("conteudo-resultados");
  carregando.style.display = "block";
  conteudo.style.display = "none";

  setTimeout(()=>{
    const encontrados = ofertas.filter(o =>
      normalizar(o.origem) === normalizar(origem) &&
      normalizar(o.destino) === normalizar(destino) &&
      (transporteSelecionado === "todos" || o.tipo === transporteSelecionado)
    );

    renderizarResultados(encontrados, origem, destino);
    carregando.style.display = "none";
    conteudo.style.display = "block";
  },650);
}

function renderizarResultados(lista, origem, destino){
  const container = document.getElementById("lista-resultados");

  if(!lista.length){
    document.getElementById("menor-preco").textContent = "—";
    document.getElementById("menor-preco-desc").textContent = "Nenhuma opção cadastrada para esta rota.";
    document.getElementById("mais-rapido").textContent = "—";
    document.getElementById("mais-rapido-desc").textContent = "Tente outra rota ou transporte.";
    document.getElementById("custo-beneficio").textContent = "—";
    document.getElementById("custo-beneficio-desc").textContent = "Nenhuma opção encontrada.";
    document.getElementById("economia").textContent = `ℹ️ Ainda não temos uma oferta cadastrada para ${origem} → ${destino}. Na versão real, os dados virão das fontes de tarifas conectadas ao sistema.`;
    const tipoMensagem = transporteSelecionado === "todos" ? "ônibus ou avião" : (transporteSelecionado === "onibus" ? "ônibus" : "avião");
    container.innerHTML = `<div class="sem-resultados"><strong>Nenhuma opção cadastrada para ${origem} → ${destino}.</strong><br><br>Não vamos mostrar empresas de outras rotas só para preencher a tela. Para esta busca, somente empresas que tiverem uma oferta específica para esse trecho serão exibidas. No sistema real, essa lista será alimentada pelas fontes de disponibilidade e tarifas.</div>`;
    return;
  }

  const porPreco = [...lista].sort((a,b)=>a.preco-b.preco);
  const porTempo = [...lista].sort((a,b)=>a.duracao-b.duracao);
  const menor = porPreco[0];
  const rapido = porTempo[0];

  /* Critério simples e transparente para o protótipo. */
  const custoBeneficio = [...lista].sort((a,b)=>{
    const scoreA = a.preco + a.duracao*0.20;
    const scoreB = b.preco + b.duracao*0.20;
    return scoreA-scoreB;
  })[0];

  document.getElementById("menor-preco").textContent = formatarMoeda(menor.preco);
  document.getElementById("menor-preco-desc").textContent = `${menor.empresa} • ${menor.tipo==="aviao"?"✈️ Avião":"🚌 Ônibus"}`;

  document.getElementById("mais-rapido").textContent = formatarDuracao(rapido.duracao);
  document.getElementById("mais-rapido-desc").textContent = `${rapido.empresa} • ${formatarMoeda(rapido.preco)}`;

  document.getElementById("custo-beneficio").textContent = formatarMoeda(custoBeneficio.preco);
  document.getElementById("custo-beneficio-desc").textContent = `${custoBeneficio.empresa} • ${formatarDuracao(custoBeneficio.duracao)}`;

  const economia = porPreco.length > 1 ? porPreco[porPreco.length-1].preco - menor.preco : 0;
  document.getElementById("economia").textContent = economia > 0
    ? `💰 Você pode economizar ${formatarMoeda(economia)} escolhendo a menor tarifa encontrada.`
    : `💰 Esta é a menor tarifa disponível entre as opções cadastradas para esta busca.`;

  container.innerHTML = lista
    .sort((a,b)=>a.preco-b.preco)
    .map((o,i)=>`
      <article class="result-card">
        <div class="result-top">
          <div>
            <div class="empresa">${o.empresa}</div>
            <div class="tipo-resultado">${o.tipo==="aviao"?"✈️ AVIÃO":"🚌 ÔNIBUS"}</div>
            ${i===0 ? '<span class="badge">🏆 Melhor preço</span>' : ''}
            ${o===rapido ? '<span class="badge">⚡ Mais rápido</span>' : ''}
          </div>
          <div class="result-info">Atualização: agora</div>
        </div>

        <div class="result-grid">
          <div>
            <strong>${origem} → ${destino}</strong>
            <div class="result-info">${o.horario} • ${formatarDuracao(o.duracao)}</div>
          </div>
          <div>
            <div class="result-info">Serviço</div>
            <strong>${o.servico}</strong>
          </div>
          <div>
            <div class="result-info">Bagagem</div>
            <strong>${o.bagagem}</strong>
          </div>
          <div>
            <div class="antigo">${formatarMoeda(o.preco*1.12)}</div>
            <div class="valor">${formatarMoeda(o.preco)}</div>
            <div class="result-info">⭐ ${o.avaliacao}</div>
          </div>
        </div>

        <div style="margin-top:17px;display:flex;justify-content:flex-end">
          <button class="btn-oficial" onclick="irParaOficial('${o.empresa}')">IR PARA O SITE OFICIAL →</button>
        </div>



      </article>
    `).join("");
}

function irParaOficial(empresa){
  const oferta = ofertas.find(o => o.empresa === empresa && o.oficial && o.oficial !== "#");
  if(oferta){
    window.open(oferta.oficial, "_blank", "noopener,noreferrer");
    return;
  }
  mostrarAviso(`O link de ${empresa} ainda será conectado.`);
}

function entrar(){
  const email = document.getElementById("email").value.trim();
  const senha = document.getElementById("senha").value;

  if(!email || !senha){
    mostrarAviso("Preencha e-mail e senha.");
    return;
  }

  mostrarAviso("Área de login em desenvolvimento. Nenhum dado foi enviado.");
}

/* Define hoje como data mínima da ida. */
const hoje = new Date();
const isoHoje = new Date(hoje.getTime() - hoje.getTimezoneOffset()*60000).toISOString().split("T")[0];
document.getElementById("ida").min = isoHoje;
document.getElementById("volta").min = isoHoje;

document.getElementById("ida").addEventListener("change",function(){
  document.getElementById("volta").min = this.value;
});
</script>
</body>
</html>

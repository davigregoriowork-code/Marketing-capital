# Marketing-capital
<!doctype html>
<html lang="pt-BR">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>Capital Market Multiplayer</title>

<style>
:root{
  --bg:#081018;
  --panel:#0d1722;
  --panel2:#111e2c;
  --line:#223347;
  --text:#e8eef5;
  --muted:#8ea0b5;
  --accent:#35d07f;
  --red:#ff6673;
  --gold:#f4c95d
}

*{box-sizing:border-box}

body{
  margin:0;
  background:var(--bg);
  color:var(--text);
  font-family:Inter,system-ui,Arial,sans-serif
}

.app{
  display:flex;
  min-height:100vh
}

.side{
  width:230px;
  background:#071019;
  border-right:1px solid var(--line);
  padding:18px;
  position:sticky;
  top:0;
  height:100vh
}

.brand{
  font-weight:800;
  font-size:21px;
  margin-bottom:4px
}

.sub{
  font-size:12px;
  color:var(--muted);
  margin-bottom:22px
}

.side button{
  display:block;
  width:100%;
  text-align:left;
  background:transparent;
  border:1px solid transparent;
  color:var(--muted);
  padding:11px;
  border-radius:8px;
  margin:4px 0;
  cursor:pointer
}

.side button.active,
.side button:hover{
  background:var(--panel2);
  color:var(--text);
  border-color:var(--line)
}

main{
  flex:1;
  min-width:0
}

.top{
  position:sticky;
  top:0;
  z-index:5;
  background:rgba(8,16,24,.94);
  backdrop-filter:blur(10px);
  border-bottom:1px solid var(--line);
  padding:10px 16px;
  display:flex;
  gap:8px;
  align-items:center;
  flex-wrap:wrap
}

.pill{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:8px;
  padding:7px 10px;
  font-size:12px;
  color:var(--muted)
}

.pill b{
  color:var(--text)
}

.speed{
  margin-left:auto;
  display:flex;
  gap:4px
}

.speed button,
.btn{
  background:var(--panel2);
  color:var(--text);
  border:1px solid var(--line);
  border-radius:7px;
  padding:8px 10px;
  cursor:pointer
}

.speed button.active{
  border-color:var(--accent);
  color:var(--accent)
}

.content{
  padding:16px
}

.grid{
  display:grid;
  grid-template-columns:repeat(4,minmax(0,1fr));
  gap:10px
}

.card,
section{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:10px;
  padding:14px;
  margin-bottom:12px
}

.card .label{
  color:var(--muted);
  font-size:12px
}

.value{
  font-size:22px;
  font-weight:750;
  margin-top:5px
}

.row{
  display:flex;
  gap:12px;
  flex-wrap:wrap
}

.col{
  flex:1;
  min-width:300px
}

h2{
  font-size:16px;
  margin:0 0 12px
}

h3{
  font-size:14px
}

.notice{
  padding:10px;
  background:#101d2a;
  border:1px solid var(--line);
  border-radius:8px;
  color:var(--muted);
  font-size:13px;
  margin-bottom:12px
}

.up{
  color:var(--accent)
}

.down{
  color:var(--red)
}

table{
  width:100%;
  border-collapse:collapse;
  font-size:13px
}

th,
td{
  padding:9px;
  border-bottom:1px solid var(--line);
  text-align:left
}

th{
  color:var(--muted);
  font-weight:600
}

.btn.buy{
  color:var(--accent)
}

.btn.sell{
  color:var(--red)
}

input,
select{
  width:100%;
  margin-top:5px;
  background:#08111b;
  border:1px solid var(--line);
  color:var(--text);
  padding:10px;
  border-radius:7px
}

.formgrid{
  display:grid;
  grid-template-columns:1fr 1fr;
  gap:9px
}

.stock{
  cursor:pointer
}

.empty{
  color:var(--muted);
  padding:20px;
  text-align:center
}

.status{
  font-size:12px
}

.online{
  color:var(--accent)
}

.offline{
  color:var(--red)
}

.toast{
  position:fixed;
  bottom:18px;
  right:18px;
  background:#122131;
  border:1px solid var(--line);
  padding:12px 15px;
  border-radius:8px;
  display:none;
  z-index:20
}

.toast.show{
  display:block
}

.modal{
  position:fixed;
  inset:0;
  background:rgba(0,0,0,.75);
  display:flex;
  align-items:center;
  justify-content:center;
  z-index:50
}

.modal.hide{
  display:none
}

.modalbox{
  background:var(--panel);
  border:1px solid var(--line);
  border-radius:12px;
  width:min(540px,94vw);
  padding:20px
}

.modalbox h1{
  margin-top:0;
  font-size:22px
}

.creator{
  border-color:var(--gold)
}

video{
  width:100%;
  max-height:300px;
  border-radius:8px;
  background:#000
}

.small{
  font-size:12px;
  color:var(--muted)
}

.locked{
  opacity:.55
}

.players{
  display:flex;
  gap:6px;
  flex-wrap:wrap
}

.playerchip{
  padding:6px 8px;
  border:1px solid var(--line);
  border-radius:99px;
  font-size:11px;
  color:var(--muted)
}

@media(max-width:800px){

  .side{
    width:62px;
    padding:8px
  }

  .side .brand,
  .side .sub,
  .side button span{
    display:none
  }

  .side button{
    text-align:center
  }

  .grid{
    grid-template-columns:1fr 1fr
  }

  .col{
    min-width:100%
  }

  .content{
    padding:10px
  }

  .speed{
    margin-left:0
  }
}

@media(max-width:520px){

  .grid{
    grid-template-columns:1fr
  }

  .formgrid{
    grid-template-columns:1fr
  }

  .top{
    padding:8px
  }

  .speed{
    width:100%;
    overflow:auto
  }
}
</style>
</head>

<body>

<div id="login" class="modal">

  <div class="modalbox">

    <h1>Capital Market</h1>

    <p>
      Entre no mercado multiplayer.
      Todos os jogadores públicos começam com US$ 500
      convertidos para a moeda do país escolhido.
    </p>

    <div class="formgrid">

      <label>
        Nome
        <input
          id="joinName"
          maxlength="24"
          placeholder="Seu nome"
        >
      </label>

      <label>
        País
        <select id="joinCountry"></select>
      </label>

    </div>

    <label style="display:block;margin-top:9px">
      Código de criador (somente para teste)

      <input
        id="creatorCode"
        placeholder="Opcional"
      >
    </label>

    <button
      class="btn buy"
      style="width:100%;margin-top:12px"
      onclick="joinGame()"
    >
      Entrar no mercado
    </button>

    <p class="small">
      Modo público: velocidade normal.
      O acesso temporário a 5x exige assistir ao vídeo de apresentação.
    </p>

  </div>

</div>


<div class="app">

  <aside class="side">

    <div class="brand">
      CAPITAL
    </div>

    <div class="sub">
      MARKET MULTIPLAYER
    </div>

    <button data-page="inicio">
      ◼ <span>Início</span>
    </button>

    <button data-page="acoes">
      ▣ <span>Ações</span>
    </button>

    <button data-page="rendafixa">
      ◆ <span>Renda Fixa</span>
    </button>

    <button data-page="moedas">
      $ <span>Moedas</span>
    </button>

    <button data-page="cripto">
      ₿ <span>Cripto</span>
    </button>

    <button data-page="banco">
      ▤ <span>Banco</span>
    </button>

    <button data-page="carteira">
      ▤ <span>Carteira</span>
    </button>

    <button data-page="jogadores">
      ● <span>Jogadores</span>
    </button>

    <button data-page="noticias">
      ! <span>Notícias</span>
    </button>

    <button data-page="economia">
      ≈ <span>Economia</span>
    </button>

  </aside>


  <main>

    <div class="top">

      <span class="pill">
        Servidor
        <b
          id="serverStatus"
          class="offline"
        >
          desconectado
        </b>
      </span>

      <span class="pill">
        Data
        <b id="clock">—</b>
      </span>

      <span class="pill">
        Saldo
        <b id="cashTop">—</b>
      </span>

      <span class="pill">
        Patrimônio
        <b id="netTop">—</b>
      </span>

      <span class="pill">
        Jogadores
        <b id="playerCount">0</b>
      </span>

      <div
        class="speed"
        id="speedBox"
      ></div>

    </div>

    <div
      class="content"
      id="pages"
    ></div>

  </main>

</div>


<div
  id="toast"
  class="toast"
></div>


<script>

'use strict';


const $ = id =>
  document.getElementById(id);


const money = (n,ccy) =>
  Number(n||0).toLocaleString(
    'pt-BR',
    {
      style:'currency',
      currency:ccy||'USD'
    }
  );


const num = n =>
  Number(n||0).toLocaleString(
    'pt-BR',
    {
      maximumFractionDigits:2
    }
  );


const esc = s =>
  String(s).replace(
    /[&<>"']/g,
    m => ({
      '&':'&amp;',
      '<':'&lt;',
      '>':'&gt;',
      '"':'&quot;',
      "'":'&#039;'
    }[m])
  );


let ws = null;
let me = null;
let state = null;
let page = 'inicio';
let speed = 1;
let videoUnlockUntil = 0;
let advanced = false;
let config = null;


function toast(m){

  $('toast').textContent = m;

  $('toast').classList.add('show');

  clearTimeout(window._toast);

  window._toast =
    setTimeout(
      () => $('toast').classList.remove('show'),
      2500
    );
}


function send(type,data){

  if(
    ws &&
    ws.readyState === 1
  ){

    ws.send(
      JSON.stringify({
        type,
        ...data
      })
    );

  }

}


function country(id){

  return state?.countries?.find(
    x => x.id === id
  ) ||
  config?.countries?.find(
    x => x.id === id
  );

}


function localPrice(usd){

  return usd *
    (country(me.country)?.fx || 1);

}


function fmt(usd){

  return money(
    localPrice(usd),
    me.ccy
  );

}


function connect(){

  const playerId =
    localStorage.getItem(
      'cm_player_id'
    );

  if(!playerId)
    return;


  const es =
    new EventSource(
      '/events?id=' +
      encodeURIComponent(playerId)
    );


  window._es = es;


  es.onopen = () => {

    $('serverStatus').textContent =
      'conectado';

    $('serverStatus').className =
      'online';

  };


  es.onerror = () => {

    $('serverStatus').textContent =
      'reconectando';

    $('serverStatus').className =
      'offline';

  };


  es.addEventListener(
    'state',
    e => {

      const d =
        JSON.parse(e.data);

      state = d;

      const np =
        d.players.find(
          x => x.id === me?.id
        );

      if(np)
        me = np;

      renderTop();
      render();

    }
  );


  es.addEventListener(
    'players',
    e => {

      if(state)
        state.players =
          JSON.parse(e.data).players;

      renderTop();

      if(page === 'jogadores')
        render();

    }
  );


  es.addEventListener(
    'trade',
    e => {

      const d =
        JSON.parse(e.data);

      if(
        d.player !== me?.name
      ){

        toast(
          `${d.player} negociou ${d.qty} ${d.ticker}`
        );

      }

    }
  );

}


async function api(url,body){

  const r =
    await fetch(
      url,
      {
        method:'POST',
        headers:{
          'Content-Type':
            'application/json',

          'x-player-id':
            localStorage.getItem(
              'cm_player_id'
            ) || ''
        },

        body:
          JSON.stringify(body)
      }
    );

  return r.json();

}


async function loadConfig(){

  config =
    await fetch(
      '/api/config'
    ).then(
      r => r.json()
    );


  $('joinCountry').innerHTML =
    config.countries.map(
      c =>
        `<option value="${c.id}">
          ${c.name} (${c.ccy}) —
          US$ 500 =
          ${money(500*c.fx,c.ccy)}
        </option>`
    ).join('');

}


async function joinGame(){

  const name =
    $('joinName')
      .value
      .trim() ||
    'Jogador';


  const c =
    $('joinCountry').value;


  const code =
    $('creatorCode')
      .value
      .trim();


  const r =
    await api(
      '/api/join',
      {
        name,
        country:c,
        creatorCode:code
      }
    );


  if(!r.ok)
    return toast(r.error);


  me = r.player;

  state = r.market;

  advanced = r.advanced;

  localStorage.setItem(
    'cm_player_id',
    me.id
  );


  $('login')
    .classList
    .add('hide');


  setupSpeed();

  connect();

  render();


  if(advanced)
    toast(
      'Modo criador ativado.'
    );

}


function setupSpeed(){

  const box =
    $('speedBox');

  box.innerHTML = '';


  const speeds =
    advanced
      ? [1,5,10,50,100]
      : [1];


  speeds.forEach(
    s => {

      const b =
        document.createElement(
          'button'
        );

      b.textContent =
        s + 'x';

      b.dataset.s =
        s;

      b.onclick =
        () => setSpeed(s);

      box.appendChild(b);

    }
  );


  markSpeed();

}


function markSpeed(){

  document
    .querySelectorAll(
      '#speedBox button'
    )
    .forEach(
      b =>
        b.classList.toggle(
          'active',
          Number(b.dataset.s)
          === speed
        )
    );

}


function setSpeed(s){

  if(
    s > 1 &&
    !advanced
  ){

    if(
      Date.now() >
      videoUnlockUntil
    ){

      openVideo();

      return;

    }

  }


  speed = s;

  markSpeed();

  toast(
    'Velocidade ' +
    s +
    'x ativa'
  );

}


function openVideo(){

  const m =
    document.createElement(
      'div'
    );


  m.className =
    'modal';


  m.id =
    'videoModal';


  m.innerHTML = `

    <div class="modalbox">

      <h2>
        Desbloquear 5x por 10 minutos
      </h2>

      <p>
        Assista ao vídeo de apresentação
        até o final. Depois, o modo 5x
        ficará disponível por 10 minutos.
      </p>

      <video
        id="promoVideo"
        controls
        playsinline
        src="/promo.mp4"
      ></video>

      <p class="small">
        Para o lançamento, coloque seu vídeo
        em <b>public/promo.mp4</b>.
      </p>

      <button
        class="btn"
        onclick="
          document
            .getElementById('videoModal')
            .remove()
        "
      >
        Fechar
      </button>

    </div>

  `;


  document.body.appendChild(m);


  $('promoVideo')
    .addEventListener(
      'ended',
      () => {

        videoUnlockUntil =
          Date.now() +
          10*60*1000;


        advanced = true;

        setupSpeed();

        speed = 5;

        markSpeed();

        m.remove();

        toast(
          '5x desbloqueado por 10 minutos.'
        );

      }
    );

}


function renderTop(){

  if(!me)
    return;


  $('cashTop').textContent =
    money(
      me.cash,
      me.ccy
    );


  $('playerCount').textContent =
    state?.players?.length ||
    1;


  const net =
    me.cash +
    (me.bank || 0) -
    (me.loans || 0) +

    Object.entries(
      me.stocks || {}
    ).reduce(
      (a,[tk,q]) =>
        a +
        q *
        (
          state.companies.find(
            c => c.ticker === tk
          )?.price || 0
        ) *
        (country(me.country)?.fx || 1),

      0
    );


  $('netTop').textContent =
    money(
      net,
      me.ccy
    );


  $('clock').textContent =
    'Tick ' +
    (state?.tick || 0);

}


function bestBid(c){

  return Math.max(
    ...c.bids.map(
      x => x.price
    ),
    c.price*.998
  );

}


function bestAsk(c){

  return Math.min(
    ...c.asks.map(
      x => x.price
    ),
    c.price*1.002
  );

}


function spark(c){

  const a =
    c.hist ||
    [c.price];

  const min =
    Math.min(...a);

  const max =
    Math.max(...a);

  const w = 420;
  const h = 120;


  const pts =
    a.map(
      (v,i) =>
        `${(i/(a.length-1||1))*w},${
          h-
          ((v-min)/(max-min||1))*h
        }`
    ).join(' ');


  return `

    <svg
      viewBox="0 0 ${w} ${h}"
      width="100%"
      height="120"
    >

      <polyline
        fill="none"
        stroke="currentColor"
        stroke-width="2"
        points="${pts}"
      />

    </svg>

  `;

}


function stockRows(list){

  return `

    <table>

      <thead>

        <tr>
          <th>Empresa</th>
          <th>Preço</th>
          <th>Variação</th>
          <th>Bid</th>
          <th>Ask</th>
        </tr>

      </thead>

      <tbody>

        ${list.map(
          c => {

            const v =
              (c.price-c.open) /
              c.open *
              100;


            return `

              <tr
                class="stock"
                onclick="
                  selectStock('${c.id}')
                "
              >

                <td>

                  ${esc(c.name)}

                  <br>

                  <span class="small">
                    ${c.ticker}
                    ·
                    ${c.country}
                  </span>

                </td>

                <td>
                  ${fmt(c.price)}
                </td>

                <td
                  class="${v>=0?'up':'down'}"
                >

                  ${v>=0?'+':''}
                  ${v.toFixed(2)}%

                </td>

                <td>
                  ${fmt(bestBid(c))}
                </td>

                <td>
                  ${fmt(bestAsk(c))}
                </td>

              </tr>

            `;

          }
        ).join('')}

      </tbody>

    </table>

  `;

}


function selectStock(id){

  page =
    'acoes';

  window.selectedStock =
    id;


  document
    .querySelectorAll(
      '.side button'
    )
    .forEach(
      b =>
        b.classList.toggle(
          'active',
          b.dataset.page === page
        )
    );


  render();

}


function pageInicio(){

  return `

    <div class="grid">

      <div class="card">

        <div class="label">
          Caixa
        </div>

        <div class="value">
          ${money(me.cash,me.ccy)}
        </div>

      </div>


      <div class="card">

        <div class="label">
          País inicial
        </div>

        <div class="value">
          ${country(me.country).name}
        </div>

      </div>


      <div class="card">

        <div class="label">
          Moeda
        </div>

        <div class="value">
          ${me.ccy}
        </div>

      </div>


      <div class="card">

        <div class="label">
          Mercado
        </div>

        <div class="value">
          Multiplayer
        </div>

      </div>

    </div>


    <div class="row">

      <div class="col">

        <section>

          <h2>
            Mercado de ações
          </h2>

          ${stockRows(
            state.companies.slice(0,10)
          )}

        </section>

      </div>


      <div class="col">

        <section>

          <h2>
            Outros jogadores
          </h2>

          <div class="players">

            ${(state.players||[])
              .map(
                p => `

                  <span
                    class="playerchip"
                  >

                    ${esc(p.name)}

                    ·

                    ${p.ccy}

                    ${
                      p.creator
                      ? ' · CRIADOR'
                      : ''
                    }

                  </span>

                `
              )
              .join('')}

          </div>

        </section>


        <section>

          <h2>
            Regras públicas
          </h2>

          <div class="notice">

            Capital inicial:
            US$ 500 convertido pela cotação
            do país escolhido.

            Ordens reais são processadas
            no servidor.

            O livro de ofertas é compartilhado
            por todos os jogadores.

          </div>

        </section>

      </div>

    </div>

  `;

}


function pageAcoes(){

  const c =
    state.companies.find(
      x =>
        x.id ===
        window.selectedStock
    ) ||
    state.companies[0];


  window.selectedStock =
    c.id;


  const owned =
    me.stocks[c.ticker] ||
    0;


  const avg =
    owned
      ? (me.stockCost[c.ticker] || 0) /
        owned
      : 0;


  return `

    <div class="row">

      <div
        class="col"
        style="flex:2"
      >

        <section>

          <h2>
            ${esc(c.name)}
            (${c.ticker})
          </h2>


          <div style="font-size:27px">

            ${fmt(c.price)}

          </div>


          <div>
            ${spark(c)}
          </div>


          <div class="row">

            <span class="pill">
              Bid
              <b>
                ${fmt(bestBid(c))}
              </b>
            </span>


            <span class="pill">
              Ask
              <b>
                ${fmt(bestAsk(c))}
              </b>
            </span>


            <span class="pill">
              Volume
              <b>
                ${num(c.volume)}
              </b>
            </span>

          </div>


          <h2 style="margin-top:15px">

            Livro de ofertas compartilhado

          </h2>


          <div class="row">

            <div class="col">

              <table>

                <thead>

                  <tr>
                    <th>Compra</th>
                    <th>Qtd.</th>
                  </tr>

                </thead>

                <tbody>

                  ${c.bids
                    .slice()
                    .sort(
                      (a,b) =>
                        b.price-a.price
                    )
                    .slice(0,8)
                    .map(
                      o => `

                        <tr>

                          <td class="up">
                            ${fmt(o.price)}
                          </td>

                          <td>
                            ${o.qty}
                          </td>

                        </tr>

                      `
                    )
                    .join('')}

                </tbody>

              </table>

            </div>


            <div class="col">

              <table>

                <thead>

                  <tr>
                    <th>Venda</th>
                    <th>Qtd.</th>
                  </tr>

                </thead>

                <tbody>

                  ${c.asks
                    .slice()
                    .sort(
                      (a,b) =>
                        a.price-b.price
                    )
                    .slice(0,8)
                    .map(
                      o => `

                        <tr>

                          <td class="down">
                            ${fmt(o.price)}
                          </td>

                          <td>
                            ${o.qty}
                          </td>

                        </tr>

                      `
                    )
                    .join('')}

                </tbody>

              </table>

            </div>

          </div>

        </section>

      </div>


      <div class="col">

        <section>

          <h2>
            Negociar
          </h2>


          <div class="notice">

            Escolha a quantidade e o tipo.

            Mercado executa contra as melhores
            ofertas disponíveis.

            Limitada só cruza o livro no
            preço definido.

          </div>


          <div class="formgrid">

            <label>

              Quantidade

              <input
                id="ordQty"
                type="number"
                min="1"
                step="1"
                value="1"
              >

            </label>


            <label>

              Tipo

              <select
                id="ordType"
                onchange="toggleLimit()"
              >

                <option value="market">
                  A mercado
                </option>

                <option value="limit">
                  Limitada
                </option>

              </select>

            </label>

          </div>


          <label
            id="limitWrap"
            style="display:none;margin-top:9px"
          >

            Preço limite (${me.ccy})

            <input
              id="ordPrice"
              type="number"
              min="0.0001"
              step="0.01"
              value="${
                (
                  c.price *
                  country(me.country).fx
                ).toFixed(2)
              }"
            >

          </label>


          <div
            class="row"
            style="margin-top:10px"
          >

            <button
              class="btn buy"
              onclick="placeOrder('buy')"
            >
              Comprar
            </button>


            <button
              class="btn sell"
              onclick="placeOrder('sell')"
            >
              Vender
            </button>

          </div>


          <div
            class="pill"
            style="margin-top:10px"
          >

            Posição:
            <b>${owned}</b>

            ·

            Preço médio:
            <b>
              ${owned ? fmt(avg) : '—'}
            </b>

          </div>

        </section>


        <section>

          <h2>
            Escolha outra empresa
          </h2>

          ${stockRows(state.companies)}

        </section>

      </div>

    </div>

  `;

}


function toggleLimit(){

  const x =
    $('ordType');


  if($('limitWrap')){

    $('limitWrap').style.display =
      x.value === 'limit'
        ? 'block'
        : 'none';

  }

}


async function placeOrder(side){

  const c =
    state.companies.find(
      x =>
        x.id ===
        window.selectedStock
    );


  const type =
    $('ordType').value;


  const qty =
    Number(
      $('ordQty').value
    );


  let price = 0;


  if(type === 'limit'){

    price =
      Number(
        $('ordPrice').value
      ) /
      country(me.country).fx;

  }


  if(
    !Number.isFinite(qty) ||
    qty < 1
  ){

    return toast(
      'Informe uma quantidade válida.'
    );

  }


  const r =
    await api(
      '/api/order',
      {
        ticker:c.ticker,
        side,
        type,
        qty,
        price
      }
    );


  if(!r.ok){

    toast(r.error);

  }else{

    toast(
      r.filled
        ? `Executado: ${r.filled} ações a ${fmt(r.price)}`
        : 'Ordem registrada.'
    );

  }

}


function pageRendaFixa(){

  return `

    <section>

      <h2>
        Renda fixa
      </h2>

      <table>

        <thead>

          <tr>
            <th>Título</th>
            <th>País</th>
            <th>Moeda</th>
            <th>Taxa</th>
            <th>Preço</th>
          </tr>

        </thead>

        <tbody>

          ${state.bonds.map(
            b => `

              <tr>

                <td>
                  ${b.issuer}
                </td>

                <td>
                  ${b.country}
                </td>

                <td>
                  ${b.ccy}
                </td>

                <td>
                  ${b.rate.toFixed(2)}%
                </td>

                <td>
                  ${fmt(b.price)}
                </td>

              </tr>

            `
          ).join('')}

        </tbody>

      </table>

    </section>

  `;

}


function pageMoedas(){

  return `

    <section>

      <h2>
        Câmbio
      </h2>

      <table>

        <thead>

          <tr>
            <th>País</th>
            <th>Moeda</th>
            <th>1 USD</th>
            <th>Juros</th>
            <th>Inflação</th>
          </tr>

        </thead>

        <tbody>

          ${state.countries.map(
            c => `

              <tr>

                <td>
                  ${c.name}
                </td>

                <td>
                  ${c.ccy}
                </td>

                <td>
                  ${c.fx.toFixed(4)}
                  ${c.ccy}
                </td>

                <td>
                  ${c.rate}%
                </td>

                <td>
                  ${c.inflation}%
                </td>

              </tr>

            `
          ).join('')}

        </tbody>

      </table>

    </section>

  `;

}


function pageCripto(){

  return `

    <section>

      <h2>
        Cripto
      </h2>

      <div class="notice">

        A camada de negociação de cripto
        pode usar o mesmo motor multiplayer
        do mercado de ações.

        Nesta versão, o foco do multiplayer
        está no livro de ações.

      </div>

    </section>

  `;

}


function pageBanco(){

  return `

    <section>

      <h2>
        Banco
      </h2>

      <div class="grid">

        <div class="card">

          <div class="label">
            Conta
          </div>

          <div class="value">
            ${money(me.bank,me.ccy)}
          </div>

        </div>


        <div class="card">

          <div class="label">
            Empréstimos
          </div>

          <div class="value">
            ${money(me.loans,me.ccy)}
          </div>

        </div>

      </div>


      <div class="notice">

        Operações bancárias ainda podem
        ser adicionadas ao protocolo do
        servidor sem alterar o mercado
        compartilhado.

      </div>

    </section>

  `;

}


function pageCarteira(){

  return `

    <section>

      <h2>
        Minha carteira
      </h2>

      <table>

        <thead>

          <tr>
            <th>Ativo</th>
            <th>Qtd.</th>
            <th>Preço atual</th>
            <th>Valor</th>
          </tr>

        </thead>

        <tbody>

          ${
            Object.entries(
              me.stocks || {}
            )
            .map(
              ([tk,q]) => {

                const c =
                  state.companies.find(
                    x =>
                      x.ticker === tk
                  );


                return c
                  ? `

                    <tr>

                      <td>
                        ${tk}
                      </td>

                      <td>
                        ${q}
                      </td>

                      <td>
                        ${fmt(c.price)}
                      </td>

                      <td>
                        ${fmt(c.price*q)}
                      </td>

                    </tr>

                  `
                  : '';

              }
            )
            .join('')
          ||
          `
            <tr>

              <td
                colspan="4"
                class="empty"
              >
                Nenhuma ação.
              </td>

            </tr>
          `}

        </tbody>

      </table>

    </section>

  `;

}


function pageJogadores(){

  return `

    <section>

      <h2>
        Mercado multiplayer
      </h2>


      <div class="notice">

        Todos os jogadores conectados
        compartilham o mesmo livro de ofertas.

        Uma compra de um jogador pode ser
        a venda de outro, e o servidor
        confirma a execução.

      </div>


      <table>

        <thead>

          <tr>
            <th>Jogador</th>
            <th>País</th>
            <th>Moeda</th>
            <th>Tipo</th>
          </tr>

        </thead>

        <tbody>

          ${(state.players||[])
            .map(
              p => `

                <tr>

                  <td>
                    ${esc(p.name)}
                  </td>

                  <td>
                    ${country(p.country).name}
                  </td>

                  <td>
                    ${p.ccy}
                  </td>

                  <td>
                    ${
                      p.creator
                        ? 'Criador'
                        : 'Jogador'
                    }
                  </td>

                </tr>

              `
            )
            .join('')}

        </tbody>

      </table>

    </section>

  `;

}


function pageNoticias(){

  return `

    <section>

      <h2>
        Notícias
      </h2>

      <p class="small">

        O feed de eventos econômicos
        será sincronizado pelo servidor
        para todos os jogadores.

      </p>

    </section>

  `;

}


function pageEconomia(){

  return `

    <section>

      <h2>
        Economia
      </h2>

      <table>

        <thead>

          <tr>
            <th>País</th>
            <th>Juros</th>
            <th>Inflação</th>
            <th>Câmbio</th>
          </tr>

        </thead>

        <tbody>

          ${state.countries.map(
            c => `

              <tr>

                <td>
                  ${c.name}
                </td>

                <td>
                  ${c.rate}%
                </td>

                <td>
                  ${c.inflation}%
                </td>

                <td>
                  ${c.fx}
                  ${c.ccy}/USD
                </td>

              </tr>

            `
          ).join('')}

        </tbody>

      </table>

    </section>

  `;

}


function render(){

  if(!state || !me)
    return;


  const f = {

    inicio:pageInicio,

    acoes:pageAcoes,

    rendafixa:pageRendaFixa,

    moedas:pageMoedas,

    cripto:pageCripto,

    banco:pageBanco,

    carteira:pageCarteira,

    jogadores:pageJogadores,

    noticias:pageNoticias,

    economia:pageEconomia

  };


  $('pages').innerHTML =
    (f[page] || pageInicio)();


  document
    .querySelectorAll(
      '.side button'
    )
    .forEach(
      b =>
        b.classList.toggle(
          'active',
          b.dataset.page === page
        )
    );


  renderTop();

}


function go(p){

  page = p;

  render();

}


document
  .querySelectorAll(
    '.side button'
  )
  .forEach(
    b =>
      b.onclick =
        () => go(b.dataset.page)
  );


loadConfig()
  .then(
    () => connect()
  );


setInterval(
  () => {

    if(
      !advanced &&
      videoUnlockUntil &&
      Date.now() >
      videoUnlockUntil
    ){

      videoUnlockUntil = 0;

      speed = 1;

      setupSpeed();

      toast(
        'O acesso temporário a 5x terminou.'
      );

    }

  },
  1000
);

</script>

</body>
</html>

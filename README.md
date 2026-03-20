<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Dashboard — Acervo Geral · GMTSS · STJ</title>
<style>a
:root {
  --bg:#f0f4f8; --card:#fff; --primary:#1a3a6b; --secondary:#2563eb;
  --cyan:#06b6d4; --green:#10b981; --yellow:#f59e0b; --red:#ef4444;
  --purple:#8b5cf6; --text:#1e293b; --muted:#64748b; --border:#e2e8f0;
  --shadow:0 2px 16px rgba(26,58,107,.08);
}
*{box-sizing:border-box;margin:0;padding:0;}
body{background:var(--bg);font-family:'Segoe UI',system-ui,sans-serif;color:var(--text);min-height:100vh;}

/* HEADER */
header{background:linear-gradient(135deg,#1a3a6b,#2563eb 60%,#06b6d4);color:#fff;box-shadow:0 4px 24px rgba(26,58,107,.22);}
.h-top{display:flex;align-items:flex-start;justify-content:space-between;padding:24px 36px;flex-wrap:wrap;gap:16px;}
.h-brand .eyebrow{font-size:.7rem;font-weight:700;letter-spacing:2px;text-transform:uppercase;opacity:.7;margin-bottom:6px;display:flex;gap:8px;}
.h-brand .eyebrow span{background:rgba(255,255,255,.15);border-radius:4px;padding:2px 8px;}
.h-brand .title{font-size:1.55rem;font-weight:800;letter-spacing:-.5px;margin-bottom:4px;}
.h-brand .sub{font-size:.8rem;opacity:.8;font-weight:500;}
.h-brand .desc{font-size:.76rem;opacity:.6;max-width:560px;line-height:1.5;margin-top:6px;}
.h-right{display:flex;flex-direction:column;gap:8px;align-items:flex-end;}
.file-row{display:flex;align-items:center;gap:8px;flex-wrap:wrap;justify-content:flex-end;}
.file-tag{display:none;align-items:center;gap:7px;background:rgba(255,255,255,.15);border:1.5px solid rgba(255,255,255,.3);border-radius:9px;padding:6px 14px;font-size:.76rem;font-weight:600;max-width:260px;}
.file-tag .fname{overflow:hidden;text-overflow:ellipsis;white-space:nowrap;max-width:160px;opacity:.9;}
.btn{display:inline-flex;align-items:center;gap:7px;padding:9px 18px;border-radius:9px;font-size:.82rem;font-weight:700;cursor:pointer;border:none;transition:all .2s;white-space:nowrap;}
.btn-load{background:#fff;color:var(--primary);box-shadow:0 2px 10px rgba(0,0,0,.15);}
.btn-load:hover{background:#dbeafe;}
.btn-remove{background:rgba(239,68,68,.8);color:#fff;border:1.5px solid rgba(255,255,255,.25);}
.btn-remove:hover{background:#dc2626;}
.btn-print{background:rgba(255,255,255,.12);color:#fff;border:1.5px solid rgba(255,255,255,.3);}
.btn-print:hover{background:rgba(255,255,255,.2);}
#fileInput{display:none;}
.h-bar{background:rgba(0,0,0,.18);padding:9px 36px;display:flex;gap:20px;flex-wrap:wrap;}
.hb{font-size:.72rem;font-weight:600;color:rgba(255,255,255,.85);display:flex;align-items:center;gap:5px;}
.hb strong{color:#fff;}

/* MAIN */
main{padding:24px 36px 48px;max-width:1700px;margin:0 auto;}

/* EMPTY */
#emptyState{display:flex;flex-direction:column;align-items:center;justify-content:center;gap:16px;padding:60px 20px;text-align:center;color:var(--muted);}
#emptyState .big{font-size:3.5rem;}
#emptyState h2{font-size:1.2rem;color:var(--text);}
#emptyState p{font-size:.86rem;max-width:460px;line-height:1.6;}
.drop-zone{
  width:100%;max-width:520px;border:2.5px dashed #93c5fd;border-radius:16px;
  padding:32px 24px;background:#eff6ff;cursor:pointer;transition:all .2s;
  display:flex;flex-direction:column;align-items:center;gap:10px;
}
.drop-zone:hover,.drop-zone.over{border-color:var(--secondary);background:#dbeafe;}
.drop-zone .dz-ic{font-size:2.6rem;}
.drop-zone .dz-t{font-size:.95rem;font-weight:700;color:var(--primary);}
.drop-zone .dz-s{font-size:.78rem;color:var(--muted);}
.dz-btn{margin-top:4px;padding:9px 26px;border-radius:9px;background:linear-gradient(135deg,#1a3a6b,#2563eb);color:#fff;border:none;font-size:.85rem;font-weight:700;cursor:pointer;box-shadow:0 4px 12px rgba(37,99,235,.3);transition:opacity .2s;}
.dz-btn:hover{opacity:.88;}
#progressWrap{width:100%;max-width:380px;display:none;flex-direction:column;align-items:center;gap:7px;}
.pbg{width:100%;height:8px;background:#dbeafe;border-radius:99px;overflow:hidden;}
.pf{height:8px;border-radius:99px;background:linear-gradient(90deg,#1a3a6b,#06b6d4);width:0%;transition:width .35s;}
#pLabel{font-size:.76rem;color:var(--secondary);font-weight:600;}
.hint-box{background:#fff;border:1px solid #bfdbfe;border-radius:10px;padding:12px 18px;font-size:.76rem;color:#475569;max-width:520px;line-height:1.7;text-align:left;}
.hint-box strong{color:var(--primary);}

/* FILTROS */
.fp{background:var(--card);border-radius:16px;box-shadow:var(--shadow);margin-bottom:22px;overflow:hidden;border:1px solid var(--border);}
.fp-head{display:flex;align-items:center;justify-content:space-between;padding:14px 22px;background:linear-gradient(135deg,#1a3a6b,#2563eb);color:#fff;cursor:pointer;user-select:none;}
.fp-head h3{font-size:.88rem;font-weight:700;display:flex;align-items:center;gap:8px;}
.f-badge{background:rgba(255,255,255,.22);border-radius:20px;padding:2px 10px;font-size:.7rem;font-weight:700;}
.fp-toggle{font-size:.76rem;background:rgba(255,255,255,.15);border-radius:7px;padding:3px 11px;}
.fp-body{padding:20px 22px 16px;}
.fsec{margin-bottom:16px;}
.fsec:last-child{margin-bottom:0;}
.fsec-lbl{font-size:.67rem;font-weight:800;color:var(--primary);text-transform:uppercase;letter-spacing:1px;margin-bottom:8px;display:flex;align-items:center;gap:8px;}
.fsec-lbl::after{content:'';flex:1;height:1px;background:var(--border);}
.frow{display:flex;gap:12px;flex-wrap:wrap;}
.fg{display:flex;flex-direction:column;gap:4px;flex:1;min-width:155px;}
.fg.w2{flex:2;min-width:220px;}
.fg.full{flex:1 1 100%;}
.fg label{font-size:.68rem;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.5px;}
.fg select,.fg input{padding:8px 11px;border-radius:8px;border:1.5px solid var(--border);font-size:.83rem;color:var(--text);background:var(--bg);outline:none;transition:border .2s,box-shadow .2s;width:100%;}
.fg select:focus,.fg input:focus{border-color:var(--secondary);box-shadow:0 0 0 3px rgba(37,99,235,.1);}
.chips-bar{display:flex;gap:7px;flex-wrap:wrap;padding:9px 22px;background:#f8faff;border-top:1px solid var(--border);}
.chip{display:inline-flex;align-items:center;gap:5px;background:#eff6ff;border:1px solid #bfdbfe;color:var(--secondary);border-radius:20px;padding:3px 11px;font-size:.71rem;font-weight:600;}
.chip-x{cursor:pointer;opacity:.55;font-size:.8rem;line-height:1;}
.chip-x:hover{opacity:1;}
.fp-actions{display:flex;gap:9px;align-items:center;flex-wrap:wrap;padding:13px 22px;background:#f1f5f9;border-top:1.5px solid var(--border);}
.btn-apply{padding:9px 24px;background:linear-gradient(135deg,#1a3a6b,#2563eb);color:#fff;border-radius:9px;border:none;font-size:.83rem;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:6px;box-shadow:0 3px 10px rgba(37,99,235,.28);transition:opacity .2s;}
.btn-apply:hover{opacity:.88;}
.btn-cf{padding:9px 18px;background:#fff;color:var(--red);border:1.5px solid var(--red);border-radius:9px;font-size:.82rem;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:6px;transition:all .2s;}
.btn-cf:hover{background:#fee2e2;}
.btn-rd{padding:9px 18px;background:#fff;color:var(--muted);border:1.5px solid var(--border);border-radius:9px;font-size:.82rem;font-weight:700;cursor:pointer;display:flex;align-items:center;gap:6px;transition:all .2s;margin-left:auto;}
.btn-rd:hover{border-color:var(--red);color:var(--red);background:#fff8f8;}

/* KPIs */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:15px;margin-bottom:22px;}
.kpi{background:var(--card);border-radius:14px;padding:20px 18px;box-shadow:var(--shadow);border-top:4px solid var(--primary);transition:transform .2s;}
.kpi:hover{transform:translateY(-3px);}
.kpi:nth-child(1){border-color:var(--secondary);}
.kpi:nth-child(2){border-color:var(--cyan);}
.kpi:nth-child(3){border-color:var(--purple);}
.kpi:nth-child(4){border-color:var(--green);}
.kpi:nth-child(5){border-color:var(--yellow);}
.kpi:nth-child(6){border-color:var(--red);}
.kpi-ic{font-size:1.4rem;margin-bottom:7px;}
.kpi-lbl{font-size:.68rem;font-weight:700;color:var(--muted);text-transform:uppercase;letter-spacing:.4px;margin-bottom:5px;}
.kpi-val{font-size:2.1rem;font-weight:800;color:var(--text);line-height:1;letter-spacing:-1px;}
.kpi-sub{font-size:.71rem;color:var(--muted);margin-top:5px;line-height:1.4;}

/* SECTION TITLE */
.stitle{font-size:.9rem;font-weight:700;color:var(--text);margin-bottom:14px;padding-bottom:9px;border-bottom:2px solid var(--border);display:flex;align-items:center;gap:9px;flex-wrap:wrap;}
.stitle .dot{width:9px;height:9px;border-radius:50%;background:linear-gradient(135deg,var(--secondary),var(--cyan));flex-shrink:0;}
.stitle .sub{font-size:.7rem;font-weight:400;color:var(--muted);}

/* GRIDS */
.g2{display:grid;grid-template-columns:1fr 1fr;gap:18px;margin-bottom:18px;}
.g3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:18px;margin-bottom:18px;}

/* CARDS */
.cc{background:var(--card);border-radius:14px;padding:22px;box-shadow:var(--shadow);}
.tc{background:var(--card);border-radius:14px;padding:22px;box-shadow:var(--shadow);margin-bottom:18px;overflow-x:auto;}
.cw{position:relative;}
.h280{height:280px;}
.h340{height:340px;}

/* TABS */
.tabs{display:flex;gap:7px;margin-bottom:18px;flex-wrap:wrap;}
.tb{padding:8px 18px;border-radius:9px;border:1.5px solid var(--border);background:var(--card);color:var(--muted);font-size:.81rem;font-weight:600;cursor:pointer;transition:all .2s;}
.tb.on{background:linear-gradient(135deg,#1a3a6b,#2563eb);color:#fff;border-color:transparent;box-shadow:0 4px 12px rgba(26,58,107,.22);}
.tb:hover:not(.on){border-color:var(--secondary);color:var(--secondary);}
.tc-body{display:none;}
.tc-body.on{display:block;}

/* TABLE */
.dt{width:100%;border-collapse:collapse;font-size:.81rem;}
.dt thead tr{background:linear-gradient(135deg,#1a3a6b,#2563eb);color:#fff;}
.dt th{padding:10px 13px;text-align:left;font-weight:600;font-size:.72rem;white-space:nowrap;}
.dt th:first-child{border-radius:7px 0 0 7px;}
.dt th:last-child{border-radius:0 7px 7px 0;}
.dt tbody tr{border-bottom:1px solid var(--border);transition:background .15s;}
.dt tbody tr:hover{background:#f8faff;}
.dt td{padding:9px 13px;}

/* BADGES */
.bd{display:inline-block;padding:2px 9px;border-radius:20px;font-size:.68rem;font-weight:700;white-space:nowrap;}
.bd-t{background:#ede9fe;color:#6d28d9;}
.bd-a{background:#dbeafe;color:#1d4ed8;}
.bd-p{background:#d1fae5;color:#065f46;}
.bd-s{background:#fef3c7;color:#92400e;}
.bd-o{background:#f1f5f9;color:#475569;}
.bd-ok{background:#d1fae5;color:#065f46;}
.bd-no{background:#fee2e2;color:#991b1b;}

/* RANK BAR */
.rb{display:flex;align-items:center;gap:7px;}
.rb-bg{flex:1;background:var(--border);border-radius:99px;height:6px;min-width:50px;}
.rb-f{height:6px;border-radius:99px;background:linear-gradient(90deg,#1a3a6b,#06b6d4);}
.rb-n{font-weight:700;font-size:.84rem;min-width:30px;text-align:right;}

/* AGING */
.ac{color:#ef4444;font-weight:700;}
.aw{color:#f59e0b;font-weight:600;}
.ag{color:#10b981;}

/* PREVIEW */
.ps{overflow-x:auto;max-height:340px;overflow-y:auto;}
.ps::-webkit-scrollbar{height:4px;width:4px;}
.ps::-webkit-scrollbar-thumb{background:var(--secondary);border-radius:99px;}

/* INFO CHIP */
.ic{display:inline-flex;align-items:center;gap:4px;background:#eff6ff;color:var(--secondary);border-radius:20px;padding:3px 9px;font-size:.7rem;font-weight:600;}

/* TOAST */
#toast{position:fixed;bottom:24px;right:24px;z-index:9999;padding:12px 20px;border-radius:11px;font-size:.83rem;font-weight:600;color:#fff;box-shadow:0 8px 28px rgba(0,0,0,.22);display:flex;align-items:center;gap:9px;transform:translateY(70px);opacity:0;transition:all .35s;pointer-events:none;}
#toast.show{transform:translateY(0);opacity:1;}

/* PRINT */
@media print{
  header .h-right,.fp,.tabs{display:none!important;}
  body{background:#fff;}
  .cc,.tc,.kpi{box-shadow:none;border:1px solid #ddd;page-break-inside:avoid;}
  main{padding:10px;}
  .g2,.g3{grid-template-columns:1fr 1fr;}
}
@media(max-width:860px){
  .h-top{padding:16px;}
  main{padding:12px;}
  .g2,.g3{grid-template-columns:1fr;}
}
</style>
</head>
<body>

<div id="toast"></div>

<!-- HEADER -->
<header>
  <div class="h-top">
    <div class="h-brand">
      <div class="eyebrow"><span>STJ</span><span>Gabinete do Ministro Teodoro Silva Santos</span></div>
      <div class="title">📊 Dashboard — Acervo Geral de Processos</div>
      <div class="sub">Gabinete do Ministro Teodoro Silva Santos &nbsp;•&nbsp; Superior Tribunal de Justiça</div>
      <div class="desc">Painel analítico de processos distribuídos até 2020. Carregue uma base Excel (.xlsx / .xls / .csv) para ativar todos os indicadores, gráficos e filtros automaticamente.</div>
    </div>
    <div class="h-right">
      <div class="file-row">
        <div class="file-tag" id="fileTag">
          📄 <span class="fname" id="fileName">—</span>
        </div>
        <input type="file" id="fileInput" accept=".xlsx,.xls,.csv">
        <button class="btn btn-load" id="btnLoad">📂 Carregar base Excel</button>
        <button class="btn btn-remove" id="btnRemove" style="display:none;" onclick="removerBase()">🗑️ Remover base</button>
      </div>
      <button class="btn btn-print" onclick="window.print()">🖨️ Imprimir / PDF</button>
    </div>
  </div>
  <div class="h-bar">
    <span class="hb">📅 Atualização: <strong id="mData">—</strong></span>
    <span class="hb">📋 Total carregado: <strong id="mTotal">—</strong></span>
    <span class="hb">👤 Responsáveis: <strong id="mUsers">—</strong></span>
    <span class="hb">🔍 Exibidos: <strong id="mFiltered">—</strong></span>
  </div>
</header>

<main>

  <!-- EMPTY STATE -->
  <div id="emptyState">
    <div class="big">⚖️</div>
    <h2>Nenhuma base carregada</h2>
    <p>Arraste um arquivo Excel para a área abaixo ou clique em <strong>Selecionar arquivo</strong>.</p>

    <div class="drop-zone" id="dropZone"
         ondragover="dzOver(event)" ondragleave="dzLeave()" ondrop="dzDrop(event)">
      <div class="dz-ic">📂</div>
      <div class="dz-t">Arraste o arquivo aqui</div>
      <div class="dz-s">Formatos aceitos: .xlsx · .xls · .csv</div>
      <button class="dz-btn" onclick="document.getElementById('fileInput').click()">Selecionar arquivo</button>
    </div>

    <div id="progressWrap">
      <div id="pLabel">Carregando...</div>
      <div class="pbg"><div class="pf" id="pFill"></div></div>
    </div>

    <div class="hint-box">
      <strong>Colunas reconhecidas automaticamente:</strong><br>
      Qdade · Registro · Processo · UF · Data de Recebimento · Dias na Unidade ·
      Processo no Gabinete · Todos os Assuntos · Tipo da Última Petição Juntada ·
      Local do Processo · Escaninho · Usuária ou Usuário Atribuído · Função · Ativo · Matéria · Observações
    </div>
  </div>

  <!-- DASHBOARD -->
  <div id="dash" style="display:none;">

    <!-- PAINEL DE FILTROS -->
    <div class="fp">
      <div class="fp-head" onclick="toggleFP()">
        <h3>🔍 Filtros de Análise <span class="f-badge" id="fBadge">0 ativos</span></h3>
        <span class="fp-toggle" id="fpToggle">▲ Recolher</span>
      </div>

      <div id="fpBody" class="fp-body">

        <!-- BUSCA TEXTUAL -->
        <div class="fsec">
          <div class="fsec-lbl">🔎 Busca textual</div>
          <div class="frow">
            <div class="fg full">
              <label>Busca em todos os campos</label>
              <input type="text" id="fTexto" placeholder="Número do processo, nome, assunto, observação...">
            </div>
          </div>
        </div>

        <!-- CLASSIFICAÇÃO -->
        <div class="fsec">
          <div class="fsec-lbl">🏷️ Classificação</div>
          <div class="frow">
            <div class="fg">
              <label>Matéria</label>
              <select id="fMateria"><option value="">Todas</option></select>
            </div>
            <div class="fg">
              <label>Função</label>
              <select id="fFuncao"><option value="">Todas</option></select>
            </div>
            <div class="fg">
              <label>Ativo</label>
              <select id="fAtivo">
                <option value="">Todos</option>
                <option value="sim">✅ Sim (Ativo)</option>
                <option value="não">❌ Não (Inativo)</option>
              </select>
            </div>
            <div class="fg">
              <label>Tipo de Petição</label>
              <select id="fPeticao"><option value="">Todos</option></select>
            </div>
          </div>
        </div>

        <!-- ORIGEM -->
        <div class="fsec">
          <div class="fsec-lbl">📍 Origem e Localização</div>
          <div class="frow">
            <div class="fg">
              <label>UF</label>
              <select id="fUF"><option value="">Todas</option></select>
            </div>
            <div class="fg w2">
              <label>Usuária ou Usuário Atribuído</label>
              <select id="fUsuario"><option value="">Todos</option></select>
            </div>
            <div class="fg">
              <label>No Gabinete</label>
              <select id="fGabinete">
                <option value="">Todos</option>
                <option value="sim">🏛️ Sim</option>
                <option value="não">📤 Não</option>
              </select>
            </div>
            <div class="fg">
              <label>Ano de Recebimento</label>
              <select id="fAno"><option value="">Todos</option></select>
            </div>
          </div>
        </div>

        <!-- OBSERVAÇÕES -->
        <div class="fsec">
          <div class="fsec-lbl">📝 Observações</div>
          <div class="frow">
            <div class="fg full">
              <label>Busca parcial em Observações</label>
              <input type="text" id="fObs" placeholder="Ex.: urgente, prazo, concluso...">
            </div>
          </div>
        </div>

      </div><!-- /fpBody -->

      <div class="chips-bar" id="chipsBar" style="display:none;"></div>

      <div class="fp-actions">
        <button class="btn-apply" onclick="aplicar()">✔ Aplicar Filtros</button>
        <button class="btn-cf"    onclick="limparFiltros()">✕ Limpar Filtros</button>
        <button class="btn-rd"    onclick="removerBase()">🗑️ Remover base e reiniciar</button>
      </div>
    </div>

    <!-- KPIs -->
    <div class="kpi-grid" id="kpiGrid"></div>

    <!-- TABS -->
    <div class="tabs">
      <button class="tb on"  onclick="tab('visao',this)">📊 Visão Geral</button>
      <button class="tb"     onclick="tab('usuarios',this)">👤 Por Usuário</button>
      <button class="tb"     onclick="tab('assuntos',this)">🏷️ Assuntos</button>
      <button class="tb"     onclick="tab('antigos',this)">⏱️ Mais Antigos</button>
      <button class="tb"     onclick="tab('lista',this)">📋 Processos</button>
      <button class="tb"     onclick="tab('preview',this)">🔍 Prévia</button>
    </div>

    <!-- TAB VISÃO GERAL -->
    <div id="tab-visao" class="tc-body on">
      <div class="g2">
        <div class="cc"><div class="stitle"><span class="dot"></span>Processos por Matéria<span class="sub">coluna Matéria</span></div><div class="cw h280"><canvas id="cMateria"></canvas></div></div>
        <div class="cc"><div class="stitle"><span class="dot"></span>No Gabinete vs. Fora<span class="sub">Processo no Gabinete</span></div><div class="cw h280"><canvas id="cGabinete"></canvas></div></div>
        <div class="cc"><div class="stitle"><span class="dot"></span>Distribuição por UF<span class="sub">Origem regional</span></div><div class="cw h280"><canvas id="cUF"></canvas></div></div>
        <div class="cc"><div class="stitle"><span class="dot"></span>Tipo da Última Petição<span class="sub">Tipo da Última Petição Juntada</span></div><div class="cw h280"><canvas id="cPeticao"></canvas></div></div>
      </div>
      <div class="g3">
        <div class="cc"><div class="stitle"><span class="dot"></span>Por Função<span class="sub">coluna Função</span></div><div class="cw h280"><canvas id="cFuncao"></canvas></div></div>
        <div class="cc"><div class="stitle"><span class="dot"></span>Ativos vs. Inativos<span class="sub">coluna Ativo</span></div><div class="cw h280"><canvas id="cAtivo"></canvas></div></div>
        <div class="cc"><div class="stitle"><span class="dot"></span>Por Ano de Recebimento<span class="sub">Data de Recebimento</span></div><div class="cw h280"><canvas id="cAno"></canvas></div></div>
      </div>
    </div>

    <!-- TAB USUÁRIOS -->
    <div id="tab-usuarios" class="tc-body">
      <div class="cc" style="margin-bottom:18px;"><div class="stitle"><span class="dot"></span>Processos por Usuário Atribuído</div><div class="cw" id="cUsrWrap"><canvas id="cUsuario"></canvas></div></div>
      <div class="tc"><div class="stitle"><span class="dot"></span>Ranking completo</div><div id="tUsuarios"></div></div>
    </div>

    <!-- TAB ASSUNTOS -->
    <div id="tab-assuntos" class="tc-body">
      <div class="cc" style="margin-bottom:18px;"><div class="stitle"><span class="dot"></span>Top 20 Assuntos<span class="sub">Todos os Assuntos — múltiplos por linha</span></div><div class="cw h340"><canvas id="cAssuntos"></canvas></div></div>
      <div class="tc"><div class="stitle"><span class="dot"></span>Lista completa</div><div id="tAssuntos"></div></div>
    </div>

    <!-- TAB MAIS ANTIGOS -->
    <div id="tab-antigos" class="tc-body">
      <div class="tc"><div class="stitle"><span class="dot"></span>Processos mais antigos <span class="ic">⚠️ Aging</span><span class="sub">Dias na Unidade</span></div><div id="tAntigos"></div></div>
    </div>

    <!-- TAB LISTA -->
    <div id="tab-lista" class="tc-body">
      <div class="tc"><div class="stitle"><span class="dot"></span>Lista de Processos <span id="cntProc" class="ic"></span></div><div id="tLista"></div></div>
    </div>

    <!-- TAB PREVIEW -->
    <div id="tab-preview" class="tc-body">
      <div class="tc"><div class="stitle"><span class="dot"></span>Prévia dos dados<span class="sub">20 primeiros registros</span></div><div class="ps" id="tPreview"></div></div>
    </div>

  </div><!-- /dash -->
</main>

<!-- SCRIPTS -->
<script>
// XLSX via CDN — carregado dinamicamente para garantir disponibilidade
(function(){
  var s=document.createElement('script');
  s.src='https://cdn.jsdelivr.net/npm/xlsx@0.18.5/dist/xlsx.full.min.js';
  s.onload=function(){ console.log('✅ XLSX carregado'); };
  s.onerror=function(){ showToast('❌ Falha ao carregar biblioteca XLSX. Verifique a conexão.','#dc2626'); };
  document.head.appendChild(s);
})();
(function(){
  var s=document.createElement('script');
  s.src='https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js';
  s.onload=function(){ console.log('✅ Chart.js carregado'); };
  document.head.appendChild(s);
})();
</script>
<script>
/* ═══════════════════════════════════════════
   ESTADO GLOBAL
═══════════════════════════════════════════ */
var DB   = [];   // dados brutos
var DF   = [];   // dados filtrados
var CM   = {};   // colMap
var CHS  = {};   // charts
var TAB  = 'visao';
var FP_OPEN = true;

/* ═══════════════════════════════════════════
   MAPEAMENTO DE COLUNAS
═══════════════════════════════════════════ */
var COLS = {
  registro:  ['registro'],
  processo:  ['processo'],
  uf:        ['uf'],
  data:      ['data de recebimento','data recebimento','datarecebimento'],
  dias:      ['dias na unidade','dias na unidade','dias'],
  gabinete:  ['processo no gabinete','no gabinete','gabinete'],
  assuntos:  ['todos os assuntos','assuntos'],
  peticao:   ['tipo da ultima peticao juntada','tipo da ultima peticao','tipo da última petição juntada','tipo da última petição','peticao','petição'],
  local:     ['local do processo','local'],
  escaninho: ['escaninho'],
  usuario:   ['usuaria ou usuario atribuido','usuária ou usuário atribuído','usuario atribuido','usuario','usuário'],
  funcao:    ['funcao','função'],
  ativo:     ['ativo'],
  materia:   ['materia','matéria'],
  obs:       ['observacoes','observações','observacao','observação','obserções']
};

function norm(s){ return (s||'').toString().normalize('NFD').replace(/[\u0300-\u036f]/g,'').toLowerCase().trim(); }

function detectCols(headers){
  CM = {};
  var hn = headers.map(norm);
  for(var k in COLS){
    var keys = COLS[k];
    for(var i=0;i<keys.length;i++){
      var nk = norm(keys[i]);
      var idx = hn.findIndex(function(h){ return h===nk || h.indexOf(nk)>=0; });
      if(idx>=0){ CM[k]=headers[idx]; break; }
    }
  }
  console.log('ColMap:', CM);
}

function g(row, key){
  var col = CM[key];
  if(!col) return '';
  var v = row[col];
  return (v!==undefined && v!==null) ? String(v).trim() : '';
}

function getAno(row){
  var dt = g(row,'data');
  if(!dt) return '';
  if(dt.indexOf('/')>=0){ var p=dt.split('/'); return (p[2]||'').substring(0,4); }
  if(dt.indexOf('-')>=0){ return dt.substring(0,4); }
  return dt.substring(0,4);
}

/* ═══════════════════════════════════════════
   UPLOAD — INPUT + DRAG AND DROP
═══════════════════════════════════════════ */
document.getElementById('btnLoad').addEventListener('click', function(){
  document.getElementById('fileInput').click();
});

document.getElementById('fileInput').addEventListener('change', function(e){
  var f = e.target.files && e.target.files[0];
  if(f) carregarArquivo(f);
  this.value='';
});

function dzOver(e){ e.preventDefault(); document.getElementById('dropZone').classList.add('over'); }
function dzLeave(){ document.getElementById('dropZone').classList.remove('over'); }
function dzDrop(e){
  e.preventDefault(); dzLeave();
  var f = e.dataTransfer && e.dataTransfer.files && e.dataTransfer.files[0];
  if(f) carregarArquivo(f);
}

function carregarArquivo(file){
  var ext = file.name.split('.').pop().toLowerCase();
  if(['xlsx','xls','csv'].indexOf(ext)<0){
    showToast('❌ Formato inválido. Use .xlsx, .xls ou .csv','#dc2626'); return;
  }
  if(typeof XLSX === 'undefined'){
    showToast('⏳ Aguarde, bibliotecas ainda carregando... Tente novamente.','#f59e0b'); return;
  }

  progresso('Lendo arquivo...', 20);

  var reader = new FileReader();
  reader.onerror = function(){
    escProgresso();
    showToast('❌ Erro ao ler o arquivo. Tente novamente.','#dc2626');
  };
  reader.onload = function(ev){
    try{
      progresso('Processando planilha...', 50);
      var data = new Uint8Array(ev.target.result);
      var wb   = XLSX.read(data, {type:'array', cellDates:true, cellText:false});
      progresso('Convertendo dados...', 75);
      var ws   = wb.Sheets[wb.SheetNames[0]];
      var raw  = XLSX.utils.sheet_to_json(ws, {defval:'', raw:false});
      if(!raw || !raw.length){
        escProgresso();
        showToast('❌ Planilha vazia ou sem dados reconhecíveis.','#dc2626'); return;
      }
      progresso('Iniciando dashboard...', 92);
      DB = raw;
      DF = raw.slice();
      detectCols(Object.keys(raw[0]));
      popularSelects();
      setTimeout(function(){
        escProgresso();
        iniciarDash(file.name);
        showToast('✅ '+raw.length.toLocaleString('pt-BR')+' processos carregados!','#1a3a6b');
      }, 300);
    } catch(err){
      escProgresso();
      console.error(err);
      showToast('❌ Erro ao processar: '+err.message,'#dc2626');
    }
  };
  reader.readAsArrayBuffer(file);
}

/* ═══════════════════════════════════════════
   PROGRESSO
═══════════════════════════════════════════ */
function progresso(msg, pct){
  var pw = document.getElementById('progressWrap');
  pw.style.display='flex';
  document.getElementById('pLabel').textContent=msg;
  document.getElementById('pFill').style.width=pct+'%';
}
function escProgresso(){
  document.getElementById('pFill').style.width='100%';
  setTimeout(function(){
    document.getElementById('progressWrap').style.display='none';
    document.getElementById('pFill').style.width='0%';
  },400);
}

/* ═══════════════════════════════════════════
   REMOVER BASE
═══════════════════════════════════════════ */
function removerBase(){
  DB=[]; DF=[]; CM={};
  destruirCharts();
  limparFiltrosUI();
  document.getElementById('dash').style.display='none';
  document.getElementById('emptyState').style.display='flex';
  document.getElementById('fileTag').style.display='none';
  document.getElementById('btnRemove').style.display='none';
  document.getElementById('kpiGrid').innerHTML='';
  document.getElementById('tPreview').innerHTML='';
  ['mData','mTotal','mUsers','mFiltered'].forEach(function(id){
    document.getElementById(id).textContent='—';
  });
  showToast('🗑️ Base removida com sucesso','#64748b');
}

/* ═══════════════════════════════════════════
   POPULAR SELECTS
═══════════════════════════════════════════ */
function uniq(key){
  var s={};
  DB.forEach(function(r){ var v=g(r,key); if(v) s[v]=1; });
  return Object.keys(s).sort();
}
function populaSel(id, items){
  var el=document.getElementById(id);
  var first=el.options[0].outerHTML;
  el.innerHTML=first+items.map(function(i){ return '<option value="'+i+'">'+i+'</option>'; }).join('');
}
function popularSelects(){
  populaSel('fMateria', uniq('materia'));
  populaSel('fFuncao',  uniq('funcao'));
  populaSel('fPeticao', uniq('peticao'));
  populaSel('fUF',      uniq('uf'));
  populaSel('fUsuario', uniq('usuario'));
  var anos = DB.map(function(r){ return getAno(r); })
    .filter(function(a){ return a.length===4 && !isNaN(+a); });
  var anosU = Object.keys(anos.reduce(function(o,a){o[a]=1;return o;},{})).sort();
  populaSel('fAno', anosU);
}

/* ═══════════════════════════════════════════
   FILTROS
═══════════════════════════════════════════ */
var FIDs = ['fTexto','fMateria','fFuncao','fAtivo','fPeticao','fUF','fUsuario','fGabinete','fAno','fObs'];
var FLBLS = {fTexto:'🔎 Busca',fMateria:'Matéria',fFuncao:'Função',fAtivo:'Ativo',
             fPeticao:'Petição',fUF:'UF',fUsuario:'Usuário',fGabinete:'Gabinete',
             fAno:'Ano',fObs:'📝 Obs'};

function vv(id){ var el=document.getElementById(id); return el ? el.value.trim() : ''; }
function vl(id){ return vv(id).toLowerCase(); }

function aplicar(){
  var ft=vl('fTexto'), fm=vl('fMateria'), ff=vl('fFuncao'), fa=vl('fAtivo'),
      fp=vl('fPeticao'), fu=vl('fUF'), fus=vl('fUsuario'), fg=vl('fGabinete'),
      fan=vv('fAno'), fo=vl('fObs');

  DF = DB.filter(function(r){
    if(fm  && g(r,'materia').toLowerCase()  !== fm)  return false;
    if(ff  && g(r,'funcao').toLowerCase()   !== ff)  return false;
    if(fa  && g(r,'ativo').toLowerCase()    !== fa)  return false;
    if(fp  && g(r,'peticao').toLowerCase()  !== fp)  return false;
    if(fu  && g(r,'uf').toLowerCase()       !== fu)  return false;
    if(fus && g(r,'usuario').toLowerCase()  !== fus) return false;
    if(fg  && g(r,'gabinete').toLowerCase() !== fg)  return false;
    if(fan && getAno(r)                     !== fan) return false;
    if(fo  && g(r,'obs').toLowerCase().indexOf(fo)<0) return false;
    if(ft){
      var linha=Object.values(r).join(' ').toLowerCase();
      if(linha.indexOf(ft)<0) return false;
    }
    return true;
  });

  atualizarBadge(); renderChips(); renderTudo();
}

function limparFiltros(){ limparFiltrosUI(); DF=DB.slice(); atualizarBadge(); renderChips(); renderTudo(); }
function limparFiltrosUI(){ FIDs.forEach(function(id){ var el=document.getElementById(id); if(el) el.value=''; }); }

function atualizarBadge(){
  var n=FIDs.filter(function(id){ return vv(id); }).length;
  var b=document.getElementById('fBadge');
  b.textContent=n+' ativo'+(n!==1?'s':'');
  b.style.background=n>0?'rgba(239,68,68,.85)':'rgba(255,255,255,.22)';
}

function renderChips(){
  var chips=FIDs.filter(function(id){ return vv(id); })
    .map(function(id){
      return '<span class="chip">'+FLBLS[id]+': <strong>'+vv(id)+'</strong>'
        +'<span class="chip-x" onclick="rmChip(\''+id+'\')">✕</span></span>';
    });
  var bar=document.getElementById('chipsBar');
  bar.style.display=chips.length?'flex':'none';
  bar.innerHTML=chips.join('');
}
function rmChip(id){ var el=document.getElementById(id); if(el) el.value=''; aplicar(); }

function toggleFP(){
  FP_OPEN=!FP_OPEN;
  document.getElementById('fpBody').style.display=FP_OPEN?'':'none';
  document.getElementById('fpToggle').textContent=FP_OPEN?'▲ Recolher':'▼ Expandir';
}

/* ═══════════════════════════════════════════
   INICIAR DASHBOARD
═══════════════════════════════════════════ */
function iniciarDash(nome){
  document.getElementById('emptyState').style.display='none';
  document.getElementById('dash').style.display='block';
  document.getElementById('fileName').textContent=nome||'Base carregada';
  document.getElementById('fileTag').style.display='flex';
  document.getElementById('btnRemove').style.display='inline-flex';
  metaAtualizar();
  renderTudo();
  renderPreview();
}

function metaAtualizar(){
  var us={}; DB.forEach(function(r){ var v=g(r,'usuario'); if(v) us[v]=1; });
  document.getElementById('mData').textContent=new Date().toLocaleDateString('pt-BR');
  document.getElementById('mTotal').textContent=DB.length.toLocaleString('pt-BR');
  document.getElementById('mUsers').textContent=Object.keys(us).length;
  document.getElementById('mFiltered').textContent=DF.length.toLocaleString('pt-BR');
}

function renderTudo(){
  destruirCharts();
  document.getElementById('mFiltered').textContent=DF.length.toLocaleString('pt-BR');
  renderKPIs();
  if(TAB==='visao')    renderVisao();
  if(TAB==='usuarios') renderUsuarios();
  if(TAB==='assuntos') renderAssuntos();
  if(TAB==='antigos')  renderAntigos();
  if(TAB==='lista')    renderLista();
  if(TAB==='preview')  renderPreview();
}

function destruirCharts(){
  for(var k in CHS){ try{ CHS[k].destroy(); }catch(e){} }
  CHS={};
}

/* ═══════════════════════════════════════════
   KPIs
═══════════════════════════════════════════ */
function renderKPIs(){
  var d=DF, tot=d.length;
  var ur={}, us={};
  d.forEach(function(r){ var v=g(r,'registro'); if(v) ur[v]=1; var u=g(r,'usuario'); if(u) us[u]=1; });
  var ativos   = d.filter(function(r){ return g(r,'ativo').toLowerCase()==='sim'; }).length;
  var noGab    = d.filter(function(r){ return g(r,'gabinete').toLowerCase()==='sim'; }).length;
  var criticos = d.filter(function(r){ var x=parseInt(g(r,'dias')); return !isNaN(x)&&x>=700; }).length;

  var kpis=[
    {i:'📋',l:'Total de Processos',    v:tot,                  s:'Contagem na seleção atual'},
    {i:'🔑',l:'Registros Únicos',       v:Object.keys(ur).length, s:'Sem duplicidade'},
    {i:'👤',l:'Responsáveis',           v:Object.keys(us).length, s:'Usuários com processos'},
    {i:'✅',l:'Processos Ativos',       v:ativos,               s:(tot-ativos).toLocaleString('pt-BR')+' inativos'},
    {i:'🏛️',l:'No Gabinete',          v:noGab,                s:((noGab/(tot||1))*100).toFixed(1)+'% do total'},
    {i:'⚠️',l:'Críticos ≥ 700 dias',  v:criticos,             s:'Aging elevado — prioridade'},
  ];
  document.getElementById('kpiGrid').innerHTML=kpis.map(function(k){
    return '<div class="kpi"><div class="kpi-ic">'+k.i+'</div>'
      +'<div class="kpi-lbl">'+k.l+'</div>'
      +'<div class="kpi-val">'+k.v.toLocaleString('pt-BR')+'</div>'
      +'<div class="kpi-sub">'+k.s+'</div></div>';
  }).join('');
}

/* ═══════════════════════════════════════════
   HELPERS CHART
═══════════════════════════════════════════ */
var PAL=['#2563eb','#06b6d4','#f59e0b','#10b981','#ef4444','#8b5cf6',
         '#ec4899','#14b8a6','#f97316','#6366f1','#84cc16','#0ea5e9',
         '#a855f7','#fb923c','#22c55e','#e11d48','#7c3aed','#0284c7'];

function cntBy(arr,fn){
  var m={};
  arr.forEach(function(r){ var k=fn(r)||'Não atribuído'; m[k]=(m[k]||0)+1; });
  return m;
}
function sortTop(obj,n){
  n=n||999;
  return Object.entries(obj).sort(function(a,b){ return b[1]-a[1]; }).slice(0,n);
}
function mkChart(id,type,labels,datasets,extra){
  if(typeof Chart==='undefined') return;
  var el=document.getElementById(id); if(!el) return;
  if(CHS[id]) CHS[id].destroy();
  CHS[id]=new Chart(el.getContext('2d'),{
    type:type,
    data:{labels:labels,datasets:datasets},
    options:Object.assign({
      responsive:true,maintainAspectRatio:false,
      plugins:{
        legend:{position:type==='bar'?'top':'right',labels:{font:{size:11},padding:11,boxWidth:13}},
        tooltip:{callbacks:{label:function(c){ return ' '+(c.parsed.y!==undefined?c.parsed.y:c.parsed).toLocaleString('pt-BR')+' proc.'; }}}
      }
    }, extra||{})
  });
}
function bdm(m){
  var l=(m||'').toLowerCase();
  if(l.indexOf('tribut')>=0) return 'bd-t';
  if(l.indexOf('admin')>=0)  return 'bd-a';
  if(l.indexOf('previd')>=0) return 'bd-p';
  if(l.indexOf('servid')>=0) return 'bd-s';
  return 'bd-o';
}

/* ═══════════════════════════════════════════
   VISÃO GERAL
═══════════════════════════════════════════ */
function renderVisao(){
  var d=DF;

  var mat=sortTop(cntBy(d,function(r){return g(r,'materia');}));
  mkChart('cMateria','doughnut',mat.map(function(e){return e[0];}),
    [{data:mat.map(function(e){return e[1];}),backgroundColor:PAL,borderWidth:2,borderColor:'#fff'}],
    {plugins:{legend:{position:'right'}}});

  var gab=sortTop(cntBy(d,function(r){return g(r,'gabinete')||'N/A';}));
  mkChart('cGabinete','pie',gab.map(function(e){return e[0];}),
    [{data:gab.map(function(e){return e[1];}),backgroundColor:['#2563eb','#10b981','#94a3b8'],borderWidth:2,borderColor:'#fff'}]);

  var uf=sortTop(cntBy(d,function(r){return g(r,'uf');}),15);
  mkChart('cUF','bar',uf.map(function(e){return e[0];}),
    [{label:'Processos',data:uf.map(function(e){return e[1];}),backgroundColor:PAL,borderRadius:6,borderSkipped:false}],
    {plugins:{legend:{display:false}},scales:{y:{beginAtZero:true,grid:{color:'#f1f5f9'}},x:{grid:{display:false}}}});

  var pet=sortTop(cntBy(d,function(r){return g(r,'peticao')||'N/A';}),12);
  mkChart('cPeticao','bar',pet.map(function(e){return e[0];}),
    [{label:'Qtde',data:pet.map(function(e){return e[1];}),backgroundColor:PAL.slice(4),borderRadius:6,borderSkipped:false}],
    {indexAxis:'y',plugins:{legend:{display:false}},scales:{x:{beginAtZero:true,grid:{color:'#f1f5f9'}},y:{grid:{display:false},ticks:{font:{size:11}}}}});

  var fn=sortTop(cntBy(d,function(r){return g(r,'funcao')||'N/A';}));
  mkChart('cFuncao','doughnut',fn.map(function(e){return e[0];}),
    [{data:fn.map(function(e){return e[1];}),backgroundColor:PAL,borderWidth:2,borderColor:'#fff'}],
    {plugins:{legend:{position:'right'}}});

  var atv=sortTop(cntBy(d,function(r){return g(r,'ativo')||'N/A';}));
  mkChart('cAtivo','pie',atv.map(function(e){return e[0];}),
    [{data:atv.map(function(e){return e[1];}),backgroundColor:['#10b981','#ef4444','#f59e0b'],borderWidth:2,borderColor:'#fff'}]);

  var am={};
  d.forEach(function(r){ var a=getAno(r); if(a.length===4&&!isNaN(+a)) am[a]=(am[a]||0)+1; });
  var ae=Object.entries(am).sort(function(a,b){return +a[0]-+b[0];});
  mkChart('cAno','line',ae.map(function(e){return e[0];}),
    [{label:'Processos',data:ae.map(function(e){return e[1];}),borderColor:'#2563eb',backgroundColor:'rgba(37,99,235,.12)',tension:.4,fill:true,pointRadius:5,pointBackgroundColor:'#2563eb'}],
    {plugins:{legend:{display:false}},scales:{y:{beginAtZero:true,grid:{color:'#f1f5f9'}},x:{grid:{display:false}}}});
}

/* ═══════════════════════════════════════════
   USUÁRIOS
═══════════════════════════════════════════ */
function renderUsuarios(){
  var d=DF;
  var usr=sortTop(cntBy(d,function(r){return g(r,'usuario')||'Não atribuído';}));
  var alt=Math.max(300,usr.length*36);
  document.getElementById('cUsrWrap').style.height=alt+'px';

  mkChart('cUsuario','bar',usr.map(function(e){return e[0];}),
    [{label:'Processos',data:usr.map(function(e){return e[1];}),backgroundColor:PAL,borderRadius:6,borderSkipped:false}],
    {indexAxis:'y',plugins:{legend:{display:false}},scales:{x:{beginAtZero:true,grid:{color:'#f1f5f9'}},y:{grid:{display:false},ticks:{font:{size:11}}}}});

  var max=usr[0]?usr[0][1]:1;
  var mm={};
  d.forEach(function(r){
    var u=g(r,'usuario')||'Não atribuído';
    var m=g(r,'materia');
    if(!mm[u]) mm[u]={};
    mm[u][m]=(mm[u][m]||0)+1;
  });

  var rows=usr.map(function(e,i){
    var s=d.find(function(r){return (g(r,'usuario')||'Não atribuído')===e[0];});
    var fn=s?g(s,'funcao'):'—';
    var at=s?g(s,'ativo'):'—';
    var mts=Object.entries(mm[e[0]]||{}).sort(function(a,b){return b[1]-a[1];})
      .map(function(m){return '<span class="bd '+bdm(m[0])+'">'+m[0]+'</span>';}).join(' ');
    return '<tr>'
      +'<td><strong>'+(i+1)+'</strong></td>'
      +'<td>'+e[0]+'</td>'
      +'<td>'+(fn||'—')+'</td>'
      +'<td><div class="rb"><div class="rb-bg"><div class="rb-f" style="width:'+(e[1]/max*100).toFixed(1)+'%"></div></div>'
      +'<span class="rb-n">'+e[1].toLocaleString('pt-BR')+'</span></div></td>'
      +'<td>'+mts+'</td>'
      +'<td><span class="bd '+(at.toLowerCase()==='sim'?'bd-ok':'bd-no')+'">'+at+'</span></td>'
      +'</tr>';
  }).join('');

  document.getElementById('tUsuarios').innerHTML='<table class="dt">'
    +'<thead><tr><th>#</th><th>Usuário</th><th>Função</th><th>Processos</th><th>Matérias</th><th>Ativo</th></tr></thead>'
    +'<tbody>'+(rows||'<tr><td colspan="6" style="text-align:center;color:var(--muted);padding:24px">Sem dados</td></tr>')+'</tbody></table>';
}

/* ═══════════════════════════════════════════
   ASSUNTOS
═══════════════════════════════════════════ */
function renderAssuntos(){
  var d=DF, cont={};
  d.forEach(function(r){
    var raw=g(r,'assuntos'); if(!raw) return;
    raw.split('\n').forEach(function(l){
      l.split(',').forEach(function(p){
        var s=p.trim().replace(/^\d+ - /,'').trim();
        if(s) cont[s]=(cont[s]||0)+1;
      });
    });
  });
  var top=sortTop(cont,20), todos=sortTop(cont);

  mkChart('cAssuntos','bar',top.map(function(e){return e[0];}),
    [{label:'Frequência',data:top.map(function(e){return e[1];}),backgroundColor:PAL,borderRadius:6,borderSkipped:false}],
    {indexAxis:'y',plugins:{legend:{display:false}},scales:{x:{beginAtZero:true,grid:{color:'#f1f5f9'}},y:{grid:{display:false},ticks:{font:{size:10}}}}});

  var mx=todos[0]?todos[0][1]:1;
  var rows=todos.map(function(e,i){
    return '<tr><td><strong>'+(i+1)+'</strong></td><td>'+e[0]+'</td>'
      +'<td><div class="rb"><div class="rb-bg"><div class="rb-f" style="width:'+(e[1]/mx*100).toFixed(1)+'%"></div></div>'
      +'<span class="rb-n">'+e[1].toLocaleString('pt-BR')+'</span></div></td></tr>';
  }).join('');
  document.getElementById('tAssuntos').innerHTML='<table class="dt">'
    +'<thead><tr><th>#</th><th>Assunto</th><th>Frequência</th></tr></thead>'
    +'<tbody>'+(rows||'<tr><td colspan="3" style="text-align:center;color:var(--muted);padding:24px">Sem dados</td></tr>')+'</tbody></table>';
}

/* ═══════════════════════════════════════════
   MAIS ANTIGOS
═══════════════════════════════════════════ */
function renderAntigos(){
  var sorted=DF.slice()
    .filter(function(r){return !isNaN(parseInt(g(r,'dias')));})
    .sort(function(a,b){return parseInt(g(b,'dias'))-parseInt(g(a,'dias'));});

  var rows=sorted.map(function(r,i){
    var dias=parseInt(g(r,'dias'));
    var cl=dias>=700?'ac':dias>=365?'aw':'ag';
    return '<tr>'
      +'<td><strong>'+(i+1)+'</strong></td>'
      +'<td><strong>'+g(r,'processo')+'</strong></td>'
      +'<td>'+g(r,'uf')+'</td>'
      +'<td class="'+cl+'">'+dias.toLocaleString('pt-BR')+'</td>'
      +'<td>'+g(r,'data')+'</td>'
      +'<td>'+g(r,'usuario')+'</td>'
      +'<td><span class="bd '+bdm(g(r,'materia'))+'">'+g(r,'materia')+'</span></td>'
      +'<td><span class="bd '+(g(r,'gabinete').toLowerCase()==='sim'?'bd-ok':'bd-no')+'">'+g(r,'gabinete')+'</span></td>'
      +'<td>'+g(r,'peticao')+'</td>'
      +'</tr>';
  }).join('');

  document.getElementById('tAntigos').innerHTML='<table class="dt">'
    +'<thead><tr><th>#</th><th>Processo</th><th>UF</th><th>Dias</th><th>Recebimento</th><th>Responsável</th><th>Matéria</th><th>Gabinete</th><th>Petição</th></tr></thead>'
    +'<tbody>'+(rows||'<tr><td colspan="9" style="text-align:center;color:var(--muted);padding:32px">Sem dados</td></tr>')+'</tbody></table>';
}

/* ═══════════════════════════════════════════
   LISTA DE PROCESSOS
═══════════════════════════════════════════ */
function renderLista(){
  var d=DF;
  document.getElementById('cntProc').textContent=d.length.toLocaleString('pt-BR')+' processo'+(d.length!==1?'s':'');

  var rows=d.slice(0,300).map(function(r){
    var dias=parseInt(g(r,'dias'));
    var cl=!isNaN(dias)?(dias>=700?'ac':dias>=365?'aw':'ag'):'';
    return '<tr>'
      +'<td><strong>'+g(r,'processo')+'</strong></td>'
      +'<td>'+g(r,'uf')+'</td>'
      +'<td class="'+cl+'">'+g(r,'dias')+'</td>'
      +'<td>'+g(r,'data')+'</td>'
      +'<td><span class="bd '+bdm(g(r,'materia'))+'">'+g(r,'materia')+'</span></td>'
      +'<td style="max-width:150px;font-size:.77rem">'+g(r,'usuario')+'</td>'
      +'<td>'+g(r,'funcao')+'</td>'
      +'<td><span class="bd '+(g(r,'gabinete').toLowerCase()==='sim'?'bd-ok':'bd-no')+'">'+g(r,'gabinete')+'</span></td>'
      +'<td>'+g(r,'peticao')+'</td>'
      +'<td><span class="bd '+(g(r,'ativo').toLowerCase()==='sim'?'bd-ok':'bd-no')+'">'+g(r,'ativo')+'</span></td>'
      +'<td style="max-width:190px;font-size:.75rem;color:var(--muted)">'+g(r,'obs')+'</td>'
      +'</tr>';
  }).join('');

  document.getElementById('tLista').innerHTML='<table class="dt">'
    +'<thead><tr><th>Processo</th><th>UF</th><th>Dias</th><th>Recebimento</th><th>Matéria</th><th>Responsável</th><th>Função</th><th>Gabinete</th><th>Petição</th><th>Ativo</th><th>Observações</th></tr></thead>'
    +'<tbody>'+(rows||'<tr><td colspan="11" style="text-align:center;color:var(--muted);padding:32px">Nenhum resultado</td></tr>')+'</tbody></table>'
    +(d.length>300?'<p style="text-align:center;color:var(--muted);font-size:.78rem;margin-top:10px">Exibindo 300 de '+d.length.toLocaleString('pt-BR')+' — refine os filtros.</p>':'');
}

/* ═══════════════════════════════════════════
   PRÉVIA
═══════════════════════════════════════════ */
function renderPreview(){
  if(!DB.length) return;
  var heads=Object.keys(DB[0]);
  var rows=DB.slice(0,20).map(function(r){
    return '<tr>'+heads.map(function(h){
      var v=r[h]||'';
      return '<td style="white-space:nowrap;max-width:180px;overflow:hidden;text-overflow:ellipsis" title="'+String(v).replace(/"/g,"'")+'">'+ v +'</td>';
    }).join('')+'</tr>';
  }).join('');
  document.getElementById('tPreview').innerHTML='<table class="dt">'
    +'<thead><tr>'+heads.map(function(h){return '<th>'+h+'</th>';}).join('')+'</tr></thead>'
    +'<tbody>'+rows+'</tbody></table>'
    +'<p style="text-align:center;color:var(--muted);font-size:.77rem;margin-top:9px">Exibindo 20 de '+DB.length.toLocaleString('pt-BR')+' registros</p>';
}

/* ═══════════════════════════════════════════
   TABS
═══════════════════════════════════════════ */
function tab(id, btn){
  TAB=id;
  document.querySelectorAll('.tc-body').forEach(function(e){ e.classList.remove('on'); });
  document.querySelectorAll('.tb').forEach(function(e){ e.classList.remove('on'); });
  document.getElementById('tab-'+id).classList.add('on');
  btn.classList.add('on');
  if(!DF.length) return;
  destruirCharts();
  renderKPIs();
  if(id==='visao')    renderVisao();
  if(id==='usuarios') renderUsuarios();
  if(id==='assuntos') renderAssuntos();
  if(id==='antigos')  renderAntigos();
  if(id==='lista')    renderLista();
  if(id==='preview')  renderPreview();
}

/* ═══════════════════════════════════════════
   TOAST
═══════════════════════════════════════════ */
function showToast(msg, bg){
  var t=document.getElementById('toast');
  t.textContent=msg;
  t.style.background=bg||'#1a3a6b';
  t.classList.add('show');
  setTimeout(function(){ t.classList.remove('show'); }, 3500);
}
</script>
</body>
</html>

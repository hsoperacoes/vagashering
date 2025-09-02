# 1) HTML COMPLETO (formulário com upload de foto e lógicas solicitadas)

> Substitua a **URL\_DO\_SEU\_WEBAPP** pelo seu endpoint publicado (Deploy > Manage deployments > Web app).

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Formulário de Candidatura – Hering Store</title>
  <style>
    :root{--bg:#121212;--card:#1b1b1b;--muted:#9aa0a6;--text:#e8eaed;--accent:#61dafb;--ok:#22c55e;--warn:#f97316}
    *{box-sizing:border-box}
    body{margin:0;font-family:system-ui,-apple-system,Segoe UI,Roboto,"Helvetica Neue",Arial,"Noto Sans",sans-serif;background:var(--bg);color:var(--text)}
    .container{max-width:1000px;margin:0 auto;padding:24px}
    .card{background:var(--card);border:1px solid #2a2a2a;border-radius:14px;padding:22px;margin-bottom:18px}
    h1{margin:0 0 14px;font-size:28px}
    h2{margin:18px 0 8px;font-size:20px;border-left:4px solid var(--accent);padding-left:10px}
    .grid{display:grid;grid-template-columns:repeat(12,1fr);gap:12px}
    .col-12{grid-column:span 12}
    .col-6{grid-column:span 6}
    .col-4{grid-column:span 4}
    .col-3{grid-column:span 3}
    label{display:block;margin-bottom:6px;color:var(--muted);font-size:14px}
    input,select,textarea{width:100%;padding:10px 12px;border:1px solid #303134;border-radius:10px;background:#0f0f10;color:var(--text)}
    textarea{min-height:90px}
    .row{display:flex;gap:12px;flex-wrap:wrap}
    .radio-group{display:flex;gap:14px;flex-wrap:wrap}
    .muted{color:var(--muted);font-size:12px}
    button, .btn{cursor:pointer;background:#0f172a;border:1px solid #243b53;border-radius:12px;color:#e2e8f0;padding:10px 14px}
    button:hover{background:#111827}
    .btn-accent{background:#0b2530;border-color:#114b5f}
    .btn-ok{background:#032d13;border-color:#0d5132}
    .btn-warn{background:#2b1608;border-color:#6b3412}
    img.preview{max-width:220px;border-radius:10px;border:2px solid #333}
    .divider{height:1px;background:#2a2a2a;margin:12px 0}
  </style>
</head>
<body>
  <div class="container">
    <div class="card">
      <h1>Formulário de Candidatura</h1>
      <p class="muted">Preencha seus dados e anexe uma foto (opcional). Campos com * são obrigatórios.</p>
      <form id="form-candidato" method="POST" action="URL_DO_SEU_WEBAPP" enctype="multipart/form-data">

        <!-- UNIDADE -->
        <h2>Unidade Escolhida</h2>
        <div class="grid">
          <div class="col-6">
            <label for="cidade">Cidade *</label>
            <input id="cidade" name="cidade" required />
          </div>
          <div class="col-6">
            <label for="filiais">Filial(is) *</label>
            <select id="filiais" name="filiais" multiple required>
              <option value="ARTUR">ARTUR</option>
              <option value="FLORIANO">FLORIANO</option>
              <option value="JOTA">JOTA</option>
              <option value="MODA">MODA</option>
              <option value="PONTO">PONTO</option>
            </select>
            <div class="muted">Segure CTRL (ou ⌘) para selecionar múltiplas.</div>
          </div>
        </div>

        <!-- DADOS PESSOAIS -->
        <h2>Dados Pessoais</h2>
        <div class="grid">
          <div class="col-6">
            <label for="nome-completo">Nome Completo *</label>
            <input id="nome-completo" name="nome-completo" required />
          </div>
          <div class="col-3">
            <label for="data-nascimento">Data de Nascimento *</label>
            <input type="date" id="data-nascimento" name="data-nascimento" required />
          </div>
          <div class="col-3">
            <label for="cpf">CPF *</label>
            <input id="cpf" name="cpf" required />
          </div>
          <div class="col-3">
            <label for="rg">RG</label>
            <input id="rg" name="rg" />
          </div>
          <div class="col-3">
            <label for="orgao-emissor">Órgão Emissor</label>
            <input id="orgao-emissor" name="orgao-emissor" />
          </div>
          <div class="col-4">
            <label for="naturalidade">Naturalidade</label>
            <input id="naturalidade" name="naturalidade" />
          </div>
          <div class="col-2">
            <label for="uf-naturalidade">UF</label>
            <input id="uf-naturalidade" name="uf-naturalidade" maxlength="2" />
          </div>
          <!-- FOTO DO CANDIDATO -->
          <div class="col-12">
            <label for="foto-candidato">Foto do candidato (JPG/PNG, até 5 MB)</label>
            <input type="file" id="foto-candidato" name="foto-candidato" accept="image/*" capture="environment" />
            <div id="preview-foto" style="margin-top:10px;display:none">
              <img id="preview-foto-img" class="preview" alt="Prévia da foto" />
            </div>
          </div>
        </div>

        <!-- ENDEREÇO -->
        <h2>Endereço</h2>
        <div class="grid">
          <div class="col-2">
            <label for="cep">CEP</label>
            <input id="cep" name="cep" />
          </div>
          <div class="col-6">
            <label for="endereco">Endereço</label>
            <input id="endereco" name="endereco" />
          </div>
          <div class="col-2">
            <label for="numero">Número</label>
            <input id="numero" name="numero" />
          </div>
          <div class="col-2">
            <label for="bairro">Bairro</label>
            <input id="bairro" name="bairro" />
          </div>
          <div class="col-6">
            <label for="municipio">Município</label>
            <input id="municipio" name="municipio" />
          </div>
          <div class="col-2">
            <label for="uf">UF</label>
            <input id="uf" name="uf" maxlength="2" />
          </div>
        </div>

        <!-- CONTATOS -->
        <h2>Contatos</h2>
        <div class="grid">
          <div class="col-4">
            <label for="celular">Celular *</label>
            <input id="celular" name="celular" required />
          </div>
          <div class="col-4">
            <label for="telefone">Telefone</label>
            <input id="telefone" name="telefone" />
          </div>
          <div class="col-4">
            <label for="email">E-mail *</label>
            <input type="email" id="email" name="email" required />
          </div>
        </div>

        <!-- FAMILIARES -->
        <h2>Informações Familiares</h2>
        <div class="grid">
          <div class="col-6">
            <label for="nome-pai">Nome do Pai</label>
            <input id="nome-pai" name="nome-pai" />
          </div>
          <div class="col-6">
            <label for="nome-mae">Nome da Mãe</label>
            <input id="nome-mae" name="nome-mae" />
          </div>
          <div class="col-3">
            <label for="estado-civil">Estado Civil</label>
            <select id="estado-civil" name="estado-civil">
              <option value="">Selecione…</option>
              <option>Solteiro(a)</option>
              <option>Casado(a)</option>
              <option>Divorciado(a)</option>
              <option>Viúvo(a)</option>
              <option>União Estável</option>
            </select>
          </div>
          <div class="col-3">
            <label for="residencia">Residência</label>
            <select id="residencia" name="residencia">
              <option value="">Selecione…</option>
              <option>Própria</option>
              <option>Alugada</option>
              <option>Com familiares</option>
            </select>
          </div>
          <!-- Fluxo de filhos conforme solicitado -->
          <div class="col-12">
            <label>Possui Filhos?</label>
            <div class="radio-group">
              <label><input type="radio" name="possui-filhos" value="sim"/> Sim</label>
              <label><input type="radio" name="possui-filhos" value="nao"/> Não</label>
            </div>

            <div id="menores-14-container" style="display:none;margin-top:10px">
              <label>Possui filhos menores de 14 anos?</label>
              <div class="radio-group">
                <label><input type="radio" name="menores-14" value="sim"/> Sim</label>
                <label><input type="radio" name="menores-14" value="nao"/> Não</label>
              </div>
            </div>

            <div id="qtd-menores-14-container" style="display:none;margin-top:10px">
              <label for="qtd-menores-14">Quantidade de filhos menores de 14 anos</label>
              <input type="number" id="qtd-menores-14" name="qtd-menores-14" min="0" disabled />
            </div>
          </div>
        </div>

        <!-- ESCOLARIDADE -->
        <h2>Escolaridade</h2>
        <div class="grid">
          <div class="col-6">
            <label for="escolaridade">Nível</label>
            <select id="escolaridade" name="escolaridade">
              <option value="">Selecione…</option>
              <option>Fundamental</option>
              <option>Médio</option>
              <option>Técnico</option>
              <option>Superior</option>
              <option>Pós / MBA</option>
              <option>Mestrado</option>
              <option>Doutorado</option>
            </select>
          </div>
        </div>

        <!-- FORMAÇÃO ACADÊMICA (dinâmica) -->
        <h2>Formação Acadêmica</h2>
        <div id="lista-cursos" class="card" style="padding:14px"></div>
        <div class="row">
          <button type="button" class="btn btn-accent" id="add-curso">+ Adicionar curso</button>
        </div>
        <input type="hidden" name="cursos" id="cursos-json" />

        <!-- INFORMAÇÕES ADICIONAIS (sem CNH e sem Línguas) -->
        <h2>Informações Adicionais</h2>
        <div class="grid">
          <div class="col-3">
            <label>Título de Eleitor</label>
            <input name="titulo-eleitor" />
          </div>
          <div class="col-2">
            <label>Zona</label>
            <input name="zona" />
          </div>
          <div class="col-4">
            <label>Condução Própria</label>
            <div class="radio-group">
              <label><input type="radio" name="conducao-propria" value="sim"/> Sim</label>
              <label><input type="radio" name="conducao-propria" value="nao"/> Não</label>
            </div>
            <div id="vale-transporte-container" style="display:none;margin-top:8px">
              <label>Precisará de vale-transporte?</label>
              <div class="radio-group">
                <label><input type="radio" name="precisa-vale-transporte" value="sim"/> Sim</label>
                <label><input type="radio" name="precisa-vale-transporte" value="nao"/> Não</label>
              </div>
            </div>
          </div>
        </div>

        <!-- EXPERIÊNCIAS -->
        <h2>Experiências Profissionais</h2>
        <div class="grid">
          <div class="col-12">
            <label>Tem experiência?</label>
            <div class="radio-group">
              <label><input type="radio" name="tem-experiencia" value="sim"/> Sim</label>
              <label><input type="radio" name="tem-experiencia" value="nao"/> Não</label>
            </div>
          </div>
        </div>
        <div id="lista-experiencias" class="card" style="padding:14px"></div>
        <div class="row">
          <button type="button" class="btn btn-accent" id="add-exp">+ Adicionar experiência</button>
        </div>
        <input type="hidden" name="experiencias" id="experiencias-json" />

        <!-- FINAIS -->
        <h2>Informações Finais</h2>
        <div class="grid">
          <div class="col-3">
            <label for="pretensao-salarial">Pretensão Salarial</label>
            <input id="pretensao-salarial" name="pretensao-salarial" />
          </div>
          <div class="col-3">
            <label for="disponibilidade-inicio">Disponibilidade para início</label>
            <input id="disponibilidade-inicio" name="disponibilidade-inicio" placeholder="Imediato / data" />
          </div>
          <div class="col-6">
            <label for="disponibilidade-horario">Disponibilidade de horário</label>
            <select id="disponibilidade-horario" name="disponibilidade-horario" multiple>
              <option>Manhã</option>
              <option>Tarde</option>
              <option>Noite</option>
              <option>Finais de semana</option>
            </select>
            <div class="muted">Você pode escolher vários.</div>
          </div>
          <div class="col-6">
            <label for="como-soube">Como soube da vaga?</label>
            <input id="como-soube" name="como-soube" />
          </div>
          <div class="col-6">
            <label>Declaração de Veracidade *</label>
            <div class="radio-group">
              <label><input type="radio" name="declaracao-veracidade" value="Li e concordo" required/> Li e concordo</label>
            </div>
          </div>
        </div>

        <div class="divider"></div>
        <div class="row">
          <button class="btn btn-ok" type="submit">Enviar candidatura</button>
          <button class="btn btn-warn" type="reset">Limpar</button>
        </div>

        <!--
          Hiddens que receberão os JSONs das listas dinâmicas
        -->
        <input type="hidden" id="_dummy"/>
      </form>
    </div>
  </div>

<script>
// ===== Preview e validação da foto =====
const fotoInput = document.getElementById('foto-candidato');
if (fotoInput) {
  fotoInput.addEventListener('change', () => {
    const file = fotoInput.files?.[0];
    const previewWrap = document.getElementById('preview-foto');
    const previewImg  = document.getElementById('preview-foto-img');

    if (!file) { previewWrap.style.display='none'; previewImg.src=''; return; }
    if (!/^image\//.test(file.type)) { alert('Envie uma imagem (JPG/PNG).'); fotoInput.value=''; return; }
    if (file.size > 5 * 1024 * 1024) { alert('Tamanho máximo: 5 MB.'); fotoInput.value=''; return; }

    const reader = new FileReader();
    reader.onload = e => { previewImg.src = e.target.result; previewWrap.style.display = 'block'; };
    reader.readAsDataURL(file);
  });
}

// ===== Fluxo Filhos -> Menores de 14 -> Quantidade =====
function setupFilhosFlow(){
  const rPossui = document.querySelectorAll('input[name="possui-filhos"]');
  const wrapMenores = document.getElementById('menores-14-container');
  const rMenores = document.querySelectorAll('input[name="menores-14"]');
  const wrapQtd = document.getElementById('qtd-menores-14-container');
  const inputQtd = document.getElementById('qtd-menores-14');

  function refresh(){
    const possui = document.querySelector('input[name="possui-filhos"]:checked')?.value;
    const menores = document.querySelector('input[name="menores-14"]:checked')?.value;

    if (possui === 'sim') {
      wrapMenores.style.display = 'block';
      if (menores === 'sim') {
        wrapQtd.style.display = 'block';
        inputQtd.disabled = false;
      } else {
        wrapQtd.style.display = 'none';
        inputQtd.disabled = true; inputQtd.value = '';
      }
    } else {
      wrapMenores.style.display = 'none';
      rMenores.forEach(r => r.checked = false);
      wrapQtd.style.display = 'none';
      inputQtd.disabled = true; inputQtd.value = '';
    }
  }

  rPossui.forEach(r => r.addEventListener('change', refresh));
  rMenores.forEach(r => r.addEventListener('change', refresh));
  refresh();
}

// ===== Fluxo Condução -> Vale-transporte =====
function setupConducao(){
  const radios = document.querySelectorAll('input[name="conducao-propria"]');
  const wrapVT = document.getElementById('vale-transporte-container');
  function refresh(){
    const v = document.querySelector('input[name="conducao-propria"]:checked')?.value;
    if (v === 'nao') wrapVT.style.display = 'block';
    else {
      wrapVT.style.display = 'none';
      document.querySelectorAll('input[name="precisa-vale-transporte"]').forEach(r=> r.checked=false);
    }
  }
  radios.forEach(r=> r.addEventListener('change', refresh));
  refresh();
}

// ===== Blocos dinâmicos: cursos =====
const listaCursos = document.getElementById('lista-cursos');
const btnAddCurso = document.getElementById('add-curso');
function renderCurso(idx, data={}){
  const el = document.createElement('div');
  el.className = 'card';
  el.style.marginBottom = '10px';
  el.innerHTML = `
    <div class="grid">
      <div class="col-5"><label>Curso</label><input data-k="curso" value="${data.curso||''}"></div>
      <div class="col-4"><label>Instituição</label><input data-k="instituicao" value="${data.instituicao||''}"></div>
      <div class="col-2"><label>Status</label><input data-k="status" value="${data.status||''}"></div>
      <div class="col-1"><label>Ano</label><input data-k="anoConclusao" value="${data.anoConclusao||''}"></div>
      <div class="col-12 row"><button type="button" class="btn btn-warn btn-del">Remover</button></div>
    </div>`;
  el.querySelector('.btn-del').onclick = () => el.remove();
  listaCursos.appendChild(el);
}
btnAddCurso?.addEventListener('click', ()=> renderCurso());

// ===== Blocos dinâmicos: experiências =====
const listaExp = document.getElementById('lista-experiencias');
const btnAddExp = document.getElementById('add-exp');
function renderExp(idx, data={}){
  const el = document.createElement('div');
  el.className = 'card';
  el.style.marginBottom = '10px';
  el.innerHTML = `
    <div class="grid">
      <div class="col-4"><label>Empresa</label><input data-k="empresa" value="${data.empresa||''}"></div>
      <div class="col-3"><label>Cargo</label><input data-k="cargo" value="${data.cargo||''}"></div>
      <div class="col-5"><label>Período (ex: 01/2022 a 03/2024)</label><input data-k="periodo" value="${data.periodo||''}"></div>
      <div class="col-4"><label>Responsável</label><input data-k="responsavel" value="${data.responsavel||''}"></div>
      <div class="col-4"><label>Contato</label><input data-k="contato" value="${data.contato||''}"></div>
      <div class="col-12"><label>Atividades</label><textarea data-k="atividades">${data.atividades||''}</textarea></div>
      <div class="col-12 row"><button type="button" class="btn btn-warn btn-del">Remover</button></div>
    </div>`;
  el.querySelector('.btn-del').onclick = () => el.remove();
  listaExp.appendChild(el);
}
btnAddExp?.addEventListener('click', ()=> renderExp());

// ===== Serialização antes de enviar =====
function serializeList(wrapper){
  const out = [];
  wrapper.querySelectorAll('.card').forEach(block=>{
    const item={};
    block.querySelectorAll('[data-k]').forEach(inp=>{
      item[inp.getAttribute('data-k')] = inp.value?.trim?.() || '';
    });
    // somente adiciona se tiver algum valor
    if (Object.values(item).some(v=>v)) out.push(item);
  });
  return out;
}

function serializeMultiSelect(sel){
  return Array.from(sel?.selectedOptions||[]).map(o=>o.value);
}

// ===== Inits =====
document.addEventListener('DOMContentLoaded', ()=>{
  setupFilhosFlow();
  setupConducao();
  // adiciona 1 bloco inicial para exemplo
  // renderCurso();
  // renderExp();

  const form = document.getElementById('form-candidato');
  form.addEventListener('submit', ()=>{
    // cursos e exp em JSON
    const cursos = serializeList(document.getElementById('lista-cursos'));
    const exp = serializeList(document.getElementById('lista-experiencias'));
    document.getElementById('cursos-json').value = JSON.stringify(cursos);
    document.getElementById('experiencias-json').value = JSON.stringify(exp);

    // disponibilidade-horario (multi) -> o Apps Script também aceita e.parameters
    const dispSel = document.getElementById('disponibilidade-horario');
    const vals = serializeMultiSelect(dispSel);
    // Truque: garantir pelo menos 1 option selecionada se usuário marcou nenhuma (opcional)
    // if (!vals.length) alert('Escolha ao menos uma disponibilidade.');
  });
});
</script>
</body>
</html>
```

---

# 2) Google Apps Script COMPLETO (recebendo foto, Drive, e PDF com imagem)

> Publique como **Web app** (Execute as: *Me* / Who has access: *Anyone*). Crie (ou informe) a pasta de fotos.

```javascript
/**
 * Web App
 * - Publish > Deploy as web app (Manage deployments)
 * - Execute as: Me
 * - Who has access: Anyone
 */

// ====== Config ======
const FOLDER_ID = ''; // Opcional: ID da pasta onde as fotos serão salvas. Vazio => cria/usa "Candidatos_Fotos".

function getFotosFolder_() {
  if (FOLDER_ID) return DriveApp.getFolderById(FOLDER_ID);
  const name = 'Candidatos_Fotos';
  const it = DriveApp.getFoldersByName(name);
  if (it.hasNext()) return it.next();
  return DriveApp.createFolder(name);
}

function doGet() {
  return ContentService.createTextOutput('OK');
}

function doPost(e) {
  try {
    if (!e || (!e.postData && !e.parameter)) {
      return jsonOut({ success: false, message: 'Nenhum dado recebido.' });
    }

    // --- Parâmetros simples/múltiplos
    var p = e.parameter || {};
    var multi = e.parameters || {};

    var filiais = [];
    if (multi['filiais'] && multi['filiais'].join) filiais = multi['filiais'];
    else if (p['filiais']) filiais = [String(p['filiais'])];

    // disponibilidade-horario pode vir múltiplo
    if (multi['disponibilidade-horario'] && multi['disponibilidade-horario'].join) {
      p['disponibilidade-horario'] = multi['disponibilidade-horario'].join(', ');
    }

    // JSONs dinâmicos
    var cursos = [];
    var experiencias = [];
    if (p.cursos)       { try { cursos       = JSON.parse(p.cursos); }       catch (_) {} }
    if (p.experiencias) { try { experiencias = JSON.parse(p.experiencias); } catch (_) {} }

    // Utils
    function val(k, dflt) { return (p[k] || dflt || '').toString().trim(); }
    function toBRDate(iso) {
      if (!iso) return '';
      var m = String(iso).match(/^(\d{4})-(\d{2})-(\d{2})$/);
      return m ? (m[3] + '/' + m[2] + '/' + m[1]) : String(iso);
    }
    function cityUF(cidade, uf) {
      var c = (cidade || '').toString().trim();
      var u = (uf || '').toString().trim();
      if (c && u) return c + ' / ' + u;
      return c || u || '';
    }
    function periodoFromExp(ex) {
      if (ex.periodo) return ex.periodo;
      var de = ex.dataEntrada || '';
      var ate = ex.dataSaida || '';
      if (de || ate) return (de || '') + (de || ate ? ' a ' : '') + (ate || '');
      return '';
    }

    // --- FOTO (se enviada)
    var fotoBlob = null;
    if (e && e.files && e.files['foto-candidato']) {
      fotoBlob = e.files['foto-candidato']; // Blob (image/*)
    }

    // --- Monta corpo do e-mail (removido CNH e Línguas estrangeiras)
    var linhas = [];

    // Unidade
    linhas.push('--- UNIDADE ESCOLHIDA ---');
    linhas.push('Cidade: ' + (val('cidade') || '-'));
    linhas.push('Filial(is): ' + (filiais.length ? filiais.join(', ') : '-'));
    linhas.push('');

    // Dados pessoais
    linhas.push('--- DADOS PESSOAIS ---');
    linhas.push('Nome Completo: ' + val('nome-completo'));
    linhas.push('Data de Nascimento: ' + toBRDate(val('data-nascimento')));
    linhas.push('CPF: ' + val('cpf'));
    linhas.push('RG / Órgão: ' + val('rg') + (val('orgao-emissor') ? ' / ' + val('orgao-emissor') : ''));
    linhas.push('Naturalidade: ' + val('naturalidade') + (val('uf-naturalidade') ? ' / ' + val('uf-naturalidade').toUpperCase() : ''));
    linhas.push('');

    // Endereço
    linhas.push('--- ENDEREÇO ---');
    linhas.push('CEP: ' + val('cep'));
    var endLinha = [val('endereco')].filter(Boolean).join('');
    if (val('numero')) endLinha += (endLinha ? ', nº ' : 'nº ') + val('numero');
    linhas.push('Endereço: ' + endLinha);
    linhas.push('Bairro: ' + val('bairro'));
    linhas.push('Município: ' + cityUF(val('municipio'), val('uf')));
    linhas.push('');

    // Contatos
    linhas.push('--- CONTATOS ---');
    linhas.push('Celular: ' + val('celular'));
    linhas.push('Telefone: ' + val('telefone'));
    linhas.push('E-mail: ' + val('email'));
    linhas.push('');

    // Familiares
    linhas.push('--- INFORMAÇÕES FAMILIARES ---');
    linhas.push('Possui Filhos: ' + (val('possui-filhos') || '-'));
    if (val('possui-filhos') === 'sim') {
      linhas.push('Menores de 14: ' + (val('menores-14') || '-'));
      if (val('menores-14') === 'sim') {
        linhas.push('Qtd menores de 14: ' + (val('qtd-menores-14') || '0'));
      }
    }
    linhas.push('');

    // Escolaridade
    linhas.push('--- ESCOLARIDADE ---');
    linhas.push('Nível: ' + (val('escolaridade') || '-'));
    linhas.push('');

    // Formação Acadêmica
    linhas.push('--- FORMAÇÃO ACADÊMICA ---');
    if (cursos && cursos.length) {
      cursos.forEach(function (c, i) {
        linhas.push('Curso ' + (i + 1) + ': ' + (c.curso || ''));
        linhas.push('  Instituição: ' + (c.instituicao || ''));
        linhas.push('  Status: ' + (c.status || ''));
        linhas.push('  Ano de conclusão: ' + (c.anoConclusao || ''));
      });
    } else {
      linhas.push('[nenhum curso informado]');
    }
    linhas.push('');

    // Adicionais
    linhas.push('--- INFORMAÇÕES ADICIONAIS ---');
    linhas.push('Condução Própria: ' + (val('conducao-propria') || '-'));
    if (val('conducao-propria') === 'nao') {
      linhas.push('Precisa de vale-transporte: ' + (val('precisa-vale-transporte') || '-'));
    }
    linhas.push('Título de Eleitor: ' + (val('titulo-eleitor') || ''));
    linhas.push('Zona: ' + (val('zona') || ''));
    linhas.push('');

    // Experiências
    linhas.push('--- EXPERIÊNCIAS PROFISSIONAIS ---');
    var temExp = (val('tem-experiencia') || '').toLowerCase();
    linhas.push('Tem Experiência: ' + (temExp || '-'));
    if (temExp === 'sim' && experiencias && experiencias.length) {
      experiencias.forEach(function (ex, i) {
        linhas.push('Experiência ' + (i + 1) + ':');
        linhas.push('  Empresa: ' + (ex.empresa || ''));
        linhas.push('  Cargo: ' + (ex.cargo || ''));
        linhas.push('  Período: ' + (periodoFromExp(ex) || '-'));
        linhas.push('  Responsável: ' + (ex.responsavel || ''));
        linhas.push('  Contato: ' + (ex.contato || ''));
        linhas.push('  Atividades: ' + (ex.atividades || ''));
      });
    } else if (temExp === 'sim') {
      linhas.push('[experiências não informadas]');
    }
    linhas.push('');

    // Finais
    linhas.push('--- INFORMAÇÕES FINAIS ---');
    linhas.push('Pretensão Salarial: ' + (val('pretensao-salarial') || '-'));
    linhas.push('Disponibilidade para Início: ' + (val('disponibilidade-inicio') || '-'));
    linhas.push('Disponibilidade de Horário: ' + (val('disponibilidade-horario') || '-'));
    linhas.push('Como soube da vaga: ' + (val('como-soube') || '-'));
    linhas.push('');

    // Declarações
    linhas.push('--- DECLARAÇÕES ---');
    linhas.push('Declaração de Veracidade: ' + (val('declaracao-veracidade') || '-'));

    var corpoEmail = linhas.join('\n');

    // --- Gera PDF com foto (se houver)
    var pdfBlob = gerarPdfCandidato_(p, cursos, experiencias, filiais, fotoBlob);

    // --- Se houver foto: salvar no Drive e anexar + link
    var fotoFile = null, fotoUrl = '';
    if (fotoBlob) {
      var folder = getFotosFolder_();
      var nomeBase = (val('nome-completo') || 'Sem_Nome').replace([^\w\s-]+/g,'_');
      var ts = Utilities.formatDate(new Date(), Session.getScriptTimeZone() || 'America/Sao_Paulo', 'yyyyMMdd_HHmmss');
      fotoBlob.setName('FOTO_' + nomeBase + '_' + ts);
      fotoFile = folder.createFile(fotoBlob);
      fotoUrl = 'https://drive.google.com/file/d/' + fotoFile.getId() + '/view';
      corpoEmail += '\n\n[Link da foto no Drive]\n' + fotoUrl;
    }

    // --- Envia e-mail
    var recipientEmail = 'hs.contratacao@gmail.com ';
    var subject = 'Nova Candidatura de Emprego - Hering Store';
    var anexos = [pdfBlob];
    if (fotoFile) anexos.push(fotoFile.getAs(fotoFile.getMimeType()));

    MailApp.sendEmail({
      to: recipientEmail,
      subject: subject,
      body: corpoEmail,
      attachments: anexos
    });

    return jsonOut({ success: true, message: 'Formulário enviado com sucesso!' });

  } catch (err) {
    return jsonOut({ success: false, message: 'Erro: ' + err });
  }
}

/**
 * Gera um PDF com os dados da candidatura (com foto opcional no topo).
 */
function gerarPdfCandidato_(dados, cursos, experiencias, filiais, fotoBlob) {
  function v(k, d) { return (dados[k] || d || '').toString().trim(); }
  function toBRDate(iso) {
    if (!iso) return '';
    var m = String(iso).match(/^(\d{4})-(\d{2})-(\d{2})$/);
    return m ? (m[3] + '/' + m[2] + '/' + m[1]) : String(iso);
  }
  function cityUF(cidade, uf) {
    var c = (cidade || '').toString().trim();
    var u = (uf || '').toString().trim();
    if (c && u) return c + ' / ' + u;
    return c || u || '';
  }
  function periodoFromExp(ex) {
    if (ex.periodo) return ex.periodo;
    var de = ex.dataEntrada || '';
    var ate = ex.dataSaida || '';
    if (de || ate) return (de || '') + (de || ate ? ' a ' : '') + (ate || '');
    return '';
  }
  function addBoldHeading(body, text) {
    return body.appendParagraph(text).setHeading(DocumentApp.ParagraphHeading.HEADING2);
  }
  function addBoldLine(body, text) {
    var para = body.appendParagraph(text);
    para.editAsText().setBold(true);
  }
  function appendKV_(body, k, val) {
    body.appendParagraph(k + ': ' + (val || ''));
  }

  var doc = DocumentApp.create('Candidatura - ' + (v('nome-completo') || 'Sem Nome'));
  var body = doc.getBody();
  body.clear();

  body.appendParagraph('CANDIDATURA - HERING STORE')
      .setHeading(DocumentApp.ParagraphHeading.HEADING1);

  // Foto no topo (se enviada)
  if (fotoBlob) {
    try {
      var img = body.appendImage(fotoBlob);
      img.setWidth(180);
      body.appendParagraph('');
    } catch (e) {
      body.appendParagraph('[Falha ao inserir foto no PDF]').setItalic(true);
    }
  }

  // Unidade
  addBoldHeading(body, '\nUnidade Escolhida');
  appendKV_(body, 'Cidade', v('cidade'));
  appendKV_(body, 'Filial(is)', (filiais && filiais.length ? filiais.join(', ') : ''));

  // Dados Pessoais
  addBoldHeading(body, '\nDados Pessoais');
  appendKV_(body, 'Nome Completo', v('nome-completo'));
  appendKV_(body, 'Data de Nascimento', toBRDate(v('data-nascimento')));
  appendKV_(body, 'CPF', v('cpf'));
  appendKV_(body, 'RG / Órgão', (v('rg') || '') + (v('orgao-emissor') ? ' / ' + v('orgao-emissor') : ''));
  appendKV_(body, 'Naturalidade', v('naturalidade') + (v('uf-naturalidade') ? ' / ' + v('uf-naturalidade').toUpperCase() : ''));

  // Endereço
  addBoldHeading(body, '\nEndereço');
  appendKV_(body, 'CEP', v('cep'));
  appendKV_(body, 'Endereço', v('endereco') + (v('numero') ? ', nº ' + v('numero') : ''));
  appendKV_(body, 'Bairro', v('bairro'));
  appendKV_(body, 'Município', cityUF(v('municipio'), v('uf')));

  // Contatos
  addBoldHeading(body, '\nContatos');
  appendKV_(body, 'Celular', v('celular'));
  appendKV_(body, 'Telefone', v('telefone'));
  appendKV_(body, 'E-mail', v('email'));

  // Familiares (fluxo solicitado)
  addBoldHeading(body, '\nInformações Familiares');
  appendKV_(body, 'Possui Filhos', v('possui-filhos'));
  if (v('possui-filhos') === 'sim') {
    appendKV_(body, 'Menores de 14', v('menores-14'));
    if (v('menores-14') === 'sim') {
      appendKV_(body, 'Qtd menores de 14', v('qtd-menores-14'));
    }
  }

  // Escolaridade
  addBoldHeading(body, '\nEscolaridade');
  appendKV_(body, 'Nível', v('escolaridade'));

  // Formação Acadêmica
  addBoldHeading(body, '\nFormação Acadêmica');
  if (cursos && cursos.length) {
    cursos.forEach(function (c, i) {
      addBoldLine(body, 'Curso ' + (i + 1));
      appendKV_(body, 'Curso', c.curso || '');
      appendKV_(body, 'Instituição', c.instituicao || '');
      appendKV_(body, 'Status', c.status || '');
      appendKV_(body, 'Ano de conclusão', c.anoConclusao || '');
      body.appendParagraph('');
    });
  } else {
    body.appendParagraph('[nenhum curso informado]').setItalic(true);
  }

  // Experiências
  addBoldHeading(body, '\nExperiências Profissionais');
  appendKV_(body, 'Tem experiência', (v('tem-experiencia') || '').toLowerCase());
  if ((v('tem-experiencia') || '').toLowerCase() === 'sim' && experiencias && experiencias.length) {
    experiencias.forEach(function (ex, i) {
      addBoldLine(body, 'Experiência ' + (i + 1));
      appendKV_(body, 'Empresa', ex.empresa || '');
      appendKV_(body, 'Cargo', ex.cargo || '');
      appendKV_(body, 'Período', periodoFromExp(ex));
      appendKV_(body, 'Responsável', ex.responsavel || '');
      appendKV_(body, 'Contato', ex.contato || '');
      appendKV_(body, 'Atividades', ex.atividades || '');
      body.appendParagraph('');
    });
  }

  // Finais
  addBoldHeading(body, '\nInformações Finais');
  appendKV_(body, 'Pretensão Salarial', v('pretensao-salarial'));
  appendKV_(body, 'Disponibilidade para Início', v('disponibilidade-inicio'));
  appendKV_(body, 'Disponibilidade de Horário', v('disponibilidade-horario'));
  appendKV_(body, 'Como soube da vaga', v('como-soube'));

  // Declarações
  addBoldHeading(body, '\nDeclarações');
  appendKV_(body, 'Declaração de Veracidade', v('declaracao-veracidade'));

  // Gera PDF
  doc.saveAndClose();
  var file = DriveApp.getFileById(doc.getId());
  var pdf = file.getAs(MimeType.PDF).setName('Candidatura - ' + (v('nome-completo') || 'Sem Nome') + '.pdf');
  file.setTrashed(true); // manter só o PDF
  return pdf;
}

// ===== Helpers =====
function jsonOut(obj) {
  return ContentService
    .createTextOutput(JSON.stringify(obj))
    .setMimeType(ContentService.MimeType.JSON);
}
```

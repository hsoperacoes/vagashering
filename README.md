
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <!-- Viewport “fixo” para manter visual do desktop no mobile -->
  <meta name="viewport" content="width=1024, initial-scale=1" />
  <title>Formulário de Solicitação de Emprego - Hering Store</title>

  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css" rel="stylesheet">

  <style>
    :root {
      --bg: #1a1a1a;
      --panel: #2a2a2a;
      --card: #3a3a3a;
      --text: #e0e0e0;
      --muted: #b0b0b0;
      --primary: #4CAF50;
      --primary-2: #45a049;
      --danger: #f44336;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body { font-family: system-ui, -apple-system, "Segoe UI", Roboto, Arial, "Noto Sans", "Helvetica Neue", sans-serif;
           background: var(--bg); color: var(--text); padding: 20px 0; }
    .container { width: 100%; max-width: 1000px; margin: 0 auto; padding: 0 20px; }

    .form-header { background: linear-gradient(135deg,#2c3e50,#34495e); color: #fff; padding: 40px 30px;
                   border-radius: 15px 15px 0 0; text-align: center; position: relative; overflow: hidden;
                   box-shadow: 0 4px 20px rgba(0,0,0,.3); }
    .form-header::before{content:"";position:absolute;inset:-50%;background:radial-gradient(circle,rgba(255,255,255,.05),transparent 70%);
                         animation: spin 30s linear infinite;}
    .form-header > * { position: relative; z-index: 1; }
    @keyframes spin { to { transform: rotate(1turn); } }
    .header-icon{ font-size: 3rem; color: var(--primary); margin-bottom: .5rem; }
    .form-header h1{ font-size: 2rem; font-weight: 800; letter-spacing: .5px; }
    .form-header h2{ font-weight: 500; opacity: .9; margin-top: .25rem; }
    .form-header p { opacity:.85; margin-top:.5rem }

    .form-container{ background: var(--panel); padding: 28px; border-radius: 0 0 15px 15px;
                     box-shadow: 0 4px 20px rgba(0,0,0,.35); }

    .form-block{ background: var(--card); border-radius: 12px; margin-bottom: 22px; border-left: 4px solid var(--primary);
                 opacity:0; transform: translateY(24px); animation: in .5s ease forwards; }
    .form-block:nth-child(1){animation-delay:.05s}.form-block:nth-child(2){animation-delay:.1s}
    .form-block:nth-child(3){animation-delay:.15s}.form-block:nth-child(4){animation-delay:.2s}
    .form-block:nth-child(5){animation-delay:.25s}.form-block:nth-child(6){animation-delay:.3s}
    .form-block:nth-child(7){animation-delay:.35s}.form-block:nth-child(8){animation-delay:.4s}
    @keyframes in{to{opacity:1; transform: none}}

    .block-header{ display:flex; align-items:center; gap:10px; background: linear-gradient(135deg,var(--primary),var(--primary-2));
                   padding: 16px 20px; border-radius: 8px 8px 0 0; }
    .block-header i{ font-size: 1.25rem }
    .block-header h3{ font-size: 1.1rem; font-weight: 700 }

    .block-content{ padding: 20px 20px 24px }

    .form-grid{ display:grid; grid-template-columns: repeat(12, 1fr); gap: 16px; }
    .col-12{ grid-column: span 12 }
    .col-8{ grid-column: span 8 } .col-6{ grid-column: span 6 } .col-4{ grid-column: span 4 } .col-3{ grid-column: span 3 }

    label{ font-weight: 700; color: var(--text); margin-bottom: 6px; font-size: .95rem }
    input[type=text], input[type=email], input[type=tel], input[type=date], input[type=number], textarea, select {
      width: 100%; background: #4a4a4a; border: 2px solid #555; color: var(--text);
      border-radius: 8px; padding: 12px 12px; font-size: .98rem; transition: .15s;
    }
    textarea{ resize: vertical; min-height: 84px }
    input:focus, textarea:focus, select:focus{ outline: none; border-color: var(--primary);
      box-shadow: 0 0 0 3px rgba(76,175,80,.2); background:#545454 }
    input:disabled, textarea:disabled{ opacity:.7; cursor:not-allowed }

    .radio-group, .checkbox-group{ display:flex; flex-wrap: wrap; gap: 12px }
    .radio-option,.checkbox-option{ display:flex; align-items:center; gap:10px; padding: 10px 14px; border-radius: 8px;
      background:#4a4a4a;border:2px solid #555; cursor:pointer; user-select:none }
    .radio-option input, .checkbox-option input{ display:none }
    .radio-custom, .checkbox-custom{ width: 18px; height: 18px; border:2px solid #777; border-radius:50%; display:inline-block }
    .checkbox-custom{ border-radius: 4px }
    .radio-option input:checked + .radio-custom{ background: var(--primary); border-color: var(--primary) }
    .checkbox-option input:checked + .checkbox-custom{ background: var(--primary); border-color: var(--primary) }
    .checkbox-option input:checked + .checkbox-custom::after{ content:"✓"; color:#fff; font-weight:700; display:block; text-align:center; line-height:18px; font-size:12px }

    .conditional-field{ margin-top: 10px; padding: 12px; border-left: 3px solid var(--primary); background: #3a3a3a; border-radius: 8px }

    .actions{ display:flex; gap:16px; justify-content:center; padding-top: 24px; border-top: 2px solid #555; margin-top: 18px }
    .btn{ border: none; border-radius: 10px; padding: 14px 26px; font-weight:800; letter-spacing:.3px; cursor:pointer;
          text-transform: uppercase; display:inline-flex; align-items:center; gap:10px; }
    .btn-primary{ background: linear-gradient(135deg,var(--primary),var(--primary-2)); color:#fff }
    .btn-danger{ background: linear-gradient(135deg,var(--danger),#d32f2f); color:#fff }

    .hidden{ display:none }

    /* Loading indicador para CEP */
    .loading-cep{ position:relative }
    .loading-cep::after{ content:""; position:absolute; right:10px; top:50%; width:16px; height:16px;
      border: 2px solid var(--primary); border-top-color: transparent; border-radius:50%; transform: translateY(-50%);
      animation: spin2 1s linear infinite; }
    @keyframes spin2 { to{ transform: translateY(-50%) rotate(1turn) } }

    .disclaimer{ font-size:.9rem; color:#ddd; opacity:.95; line-height:1.6 }
    .muted{ color: var(--muted) }
  </style>
</head>

<body>
  <div class="container">
    <header class="form-header">
      <i class="fas fa-briefcase header-icon"></i>
      <h1>FORMULÁRIO DE SOLICITAÇÃO DE EMPREGO</h1>
      <h2>HERING STORE</h2>
      <p>Preencha todos os campos para que sua candidatura seja validada.</p>
    </header>

    <div class="form-container">
      <form id="job-form" action="https://script.google.com/macros/s/AKfycbzdMkDG0N6xwF_px9n2N2gqqGFjYyv0D_8jOtremC3WSFQBy57_tHwtBg8CEsf-G93N/exec" method="POST" novalidate>

        <!-- 1. Dados pessoais -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-user"></i><h3>Dados Pessoais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-12">
                <label for="nome">Nome Completo *</label>
                <input id="nome" name="nome" type="text" required />
              </div>

              <div class="col-4">
                <label for="nascimento">Data de Nascimento *</label>
                <input id="nascimento" name="data-nascimento" type="date" required />
              </div>

              <div class="col-4">
                <label for="rg">RG *</label>
                <input id="rg" name="rg" type="text" required />
              </div>

              <div class="col-4">
                <label for="orgao-emissor">Órgão Emissor *</label>
                <input id="orgao-emissor" name="orgao-emissor" type="text" required />
              </div>

              <div class="col-4">
                <label for="cpf">CPF *</label>
                <input type="text" id="cpf" name="cpf" placeholder="000.000.000-00"
                       inputmode="numeric" autocomplete="off" maxlength="14"
                       pattern="[0-9]{3}\.[0-9]{3}\.[0-9]{3}-[0-9]{2}" title="Use o formato 000.000.000-00" required />
              </div>

              <div class="col-4">
                <label for="naturalidade">Naturalidade *</label>
                <input id="naturalidade" name="naturalidade" type="text" required />
              </div>

              <div class="col-4">
                <label for="uf-nat">UF *</label>
                <input id="uf-nat" name="uf-naturalidade" type="text" maxlength="2" required />
              </div>
            </div>
          </div>
        </section>

        <!-- 2. Endereço -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-map-marker-alt"></i><h3>Endereço</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-3">
                <label for="cep">CEP *</label>
                <input id="cep" name="cep" placeholder="00000-000" inputmode="numeric" maxlength="9"
                       pattern="[0-9]{5}-?[0-9]{3}" required />
              </div>
              <div class="col-7">
                <label for="endereco">Endereço *</label>
                <input id="endereco" name="endereco" type="text" required readonly />
              </div>
              <div class="col-2">
                <label for="numero">Nº *</label>
                <input id="numero" name="numero" type="text" required />
              </div>
              <div class="col-4">
                <label for="bairro">Bairro *</label>
                <input id="bairro" name="bairro" type="text" required readonly />
              </div>
              <div class="col-4">
                <label for="municipio">Município *</label>
                <input id="municipio" name="municipio" type="text" required readonly />
              </div>
              <div class="col-4">
                <label for="uf">UF *</label>
                <input id="uf" name="uf" type="text" maxlength="2" required readonly />
              </div>
            </div>
          </div>
        </section>

        <!-- 3. Contatos -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-phone"></i><h3>Contatos Pessoais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-4">
                <label for="telefone">Telefone</label>
                <input id="telefone" name="telefone" type="tel" placeholder="(00) 0000-0000" />
              </div>
              <div class="col-4">
                <label for="celular">Celular *</label>
                <input id="celular" name="celular" type="tel" placeholder="(00) 00000-0000" required />
              </div>
              <div class="col-12">
                <label for="email">E-mail *</label>
                <input id="email" name="email" type="email" required />
              </div>
            </div>
          </div>
        </section>

        <!-- 4. Familia -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-users"></i><h3>Informações Familiares</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-6">
                <label for="nome-pai">Nome do Pai</label>
                <input id="nome-pai" name="nome-pai" type="text" />
              </div>
              <div class="col-6">
                <label for="nome-mae">Nome da Mãe *</label>
                <input id="nome-mae" name="nome-mae" type="text" required />
              </div>

              <div class="col-12">
                <label>Estado Civil *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="estado-civil" value="casado" required /><span class="radio-custom"></span>Casado(a)</label>
                  <label class="radio-option"><input type="radio" name="estado-civil" value="solteiro" required /><span class="radio-custom"></span>Solteiro(a)</label>
                  <label class="radio-option"><input type="radio" name="estado-civil" value="divorciado" required /><span class="radio-custom"></span>Divorciado(a)</label>
                </div>
              </div>

              <div class="col-12">
                <label>Residência *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="residencia" value="propria" required /><span class="radio-custom"></span>Própria</label>
                  <label class="radio-option"><input type="radio" name="residencia" value="alugada" required /><span class="radio-custom"></span>Alugada</label>
                </div>
              </div>

              <div class="col-12">
                <label>Possui Filhos?</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="possui-filhos" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="possui-filhos" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>
                <div id="filhos-extra" class="conditional-field hidden">
                  <div class="form-grid">
                    <div class="col-4">
                      <label for="qtd-filhos">Quantos filhos?</label>
                      <input id="qtd-filhos" name="quantidade-filhos" type="number" min="0" />
                    </div>
                    <div class="col-8">
                      <label>Menores de 14 anos</label>
                      <div class="radio-group">
                        <label class="radio-option"><input type="radio" name="menores-14" value="sim" /><span class="radio-custom"></span>Sim</label>
                        <label class="radio-option"><input type="radio" name="menores-14" value="nao" /><span class="radio-custom"></span>Não</label>
                      </div>
                    </div>
                  </div>
                </div>
              </div>

            </div>
          </div>
        </section>

        <!-- 5. Escolaridade -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-graduation-cap"></i><h3>Grau de Escolaridade</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-12">
                <label>Selecione seu nível de escolaridade *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="escolaridade" value="fundamental-completo" required /><span class="radio-custom"></span>Ensino Fundamental Completo</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="fundamental-incompleto" required /><span class="radio-custom"></span>Ensino Fundamental Incompleto</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="medio-completo" required /><span class="radio-custom"></span>Ensino Médio Completo</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="medio-incompleto" required /><span class="radio-custom"></span>Ensino Médio Incompleto</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="superior-completo" required /><span class="radio-custom"></span>Ensino Superior Completo</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="superior-incompleto" required /><span class="radio-custom"></span>Ensino Superior Incompleto</label>
                </div>
              </div>
            </div>
          </div>
        </section>

        <!-- 6. Formação acadêmica dinâmica -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-certificate"></i><h3>Formação Acadêmica</h3></div>
          <div class="block-content">
            <label class="checkbox-option">
              <input type="checkbox" id="tem-formacao" />
              <span class="checkbox-custom"></span> Possuo formação acadêmica (cursos técnicos, superiores, pós-graduação, etc.)
            </label>

            <div id="formacao-wrap" class="hidden" style="margin-top:14px">
              <div id="cursos"></div>
              <div class="actions" style="border:0; padding-top:12px; margin-top:0; justify-content:flex-start">
                <button type="button" id="add-curso" class="btn btn-primary"><i class="fa fa-plus"></i> Adicionar curso</button>
              </div>
            </div>
          </div>
        </section>

        <!-- 7. Informações adicionais -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-info-circle"></i><h3>Informações Adicionais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-4">
                <label for="titulo-eleitor">Título de Eleitor nº</label>
                <input id="titulo-eleitor" name="titulo-eleitor" type="text" />
              </div>
              <div class="col-4">
                <label for="zona">Zona</label>
                <input id="zona" name="zona" type="text" />
              </div>

              <div class="col-12">
                <label>CNH</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="cnh" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="cnh" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>
                <div id="cnh-extra" class="conditional-field hidden">
                  <label for="categoria-cnh">Categoria</label>
                  <input id="categoria-cnh" name="categoria-cnh" type="text" />
                </div>
              </div>

              <div class="col-12">
                <label>Condução Própria</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="conducao-propria" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="conducao-propria" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>
              </div>

              <div class="col-12">
                <label>Possui alguma deficiência</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="deficiencia" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="deficiencia" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>
              </div>

              <div class="col-12">
                <label>Línguas estrangeiras</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="linguas-estrangeiras" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="linguas-estrangeiras" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>
                <div id="linguas-extra" class="conditional-field hidden">
                  <label for="quais-linguas">Quais línguas?</label>
                  <input id="quais-linguas" name="quais-linguas" type="text" />
                </div>
              </div>

              <div class="col-12">
                <label>Conhecimento de Informática</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="informatica" value="basico" /><span class="radio-custom"></span>Básico</label>
                  <label class="radio-option"><input type="radio" name="informatica" value="intermediario" /><span class="radio-custom"></span>Intermediário</label>
                  <label class="radio-option"><input type="radio" name="informatica" value="avancado" /><span class="radio-custom"></span>Avançado</label>
                </div>
              </div>
            </div>
          </div>
        </section>

        <!-- 8. Experiências -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-history"></i><h3>Experiências Profissionais</h3></div>
          <div class="block-content">
            <label class="radio-option">
              <input type="radio" name="tem-experiencia" value="sim" />
              <span class="radio-custom"></span> Possuo experiência profissional
            </label>
            <label class="radio-option" style="margin-left:12px">
              <input type="radio" name="tem-experiencia" value="nao" />
              <span class="radio-custom"></span> Não possuo experiência profissional
            </label>

            <div id="xp-wrap" class="hidden" style="margin-top:14px">
              <div id="experiencias"></div>
              <div class="actions" style="border:0; padding-top:12px; margin-top:0; justify-content:flex-start">
                <button type="button" id="add-xp" class="btn btn-primary"><i class="fa fa-plus"></i> Adicionar experiência</button>
              </div>
            </div>
          </div>
        </section>

        <!-- 9. Finais -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-clipboard-check"></i><h3>Informações Finais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="col-4">
                <label for="pretensao">Pretensão Salarial</label>
                <input id="pretensao" name="pretensao-salarial" type="text" placeholder="R$ 0.000,00" />
              </div>
              <div class="col-4">
                <label for="inicio">Disponibilidade para Início</label>
                <input id="inicio" name="disponibilidade-inicio" type="text" />
              </div>
              <div class="col-12">
                <label>Disponibilidade de Horário (escolha 1)</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="manha" /><span class="radio-custom"></span>Manhã</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="tarde" /><span class="radio-custom"></span>Tarde</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="noite" /><span class="radio-custom"></span>Noite</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="integral" /><span class="radio-custom"></span>Integral</label>
                </div>
              </div>
              <div class="col-12">
                <label>Como soube da vaga?</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="como-soube" value="site" /><span class="radio-custom"></span>Site de Empregos</label>
                  <label class="radio-option"><input type="radio" name="como-soube" value="indicacao" /><span class="radio-custom"></span>Indicação</label>
                  <label class="radio-option"><input type="radio" name="como-soube" value="redes-sociais" /><span class="radio-custom"></span>Redes Sociais</label>
                  <label class="radio-option"><input type="radio" name="como-soube" value="outro" /><span class="radio-custom"></span>Outro</label>
                </div>
              </div>
            </div>

            <div style="margin-top:14px" class="disclaimer">
              <strong>Declaração de Confidencialidade:</strong> Seus dados serão usados exclusivamente para fins de recrutamento e seleção,
              tratados com segurança e não serão compartilhados com terceiros sem seu consentimento.
            </div>
          </div>
        </section>

        <!-- 10. Declaração de veracidade -->
        <section class="form-block">
          <div class="block-header"><i class="fas fa-file-signature"></i><h3>Declaração de Veracidade</h3></div>
          <div class="block-content">
            <label class="checkbox-option" style="align-items:flex-start">
              <input type="checkbox" id="veracidade" name="declaracao-veracidade" />
              <span class="checkbox-custom"></span>
              <span class="disclaimer">
                Declaro que as informações prestadas neste formulário são verdadeiras e completas, assumindo total responsabilidade pelas mesmas.
                Estou ciente de que a falsidade das informações poderá implicar na desclassificação do processo seletivo, sem prejuízo das medidas legais cabíveis.
              </span>
            </label>
          </div>
        </section>

        <div class="actions">
          <button type="submit" class="btn btn-primary"><i class="fa fa-paper-plane"></i> Enviar Candidatura</button>
          <button type="reset" class="btn btn-danger"><i class="fa fa-eraser"></i> Limpar Formulário</button>
        </div>
      </form>
    </div>
  </div>

  <script>
    // ---------- Utilidades de máscara ----------
    function formatCPF(value){
      const d = value.replace(/\\D/g,'').slice(0,11);
      const p=[]; if(d.length>0)p.push(d.slice(0,3)); if(d.length>3)p.push(d.slice(3,6)); if(d.length>6)p.push(d.slice(6,9));
      let out=p.join('.'); if(d.length>9) out += '-' + d.slice(9,11); return out;
    }
    function isCPFFormatted(v){ return /^\\d{3}\\.\\d{3}\\.\\d{3}-\\d{2}$/.test(v); }

    // Pretensão salarial
    function formatMoneyBR(v){
      const n = v.replace(/\\D/g,''); if(!n) return '';
      return (parseInt(n,10)/100).toLocaleString('pt-BR',{style:'currency', currency:'BRL'});
    }

    // Telefone
    function maskPhone(v){
      const d=v.replace(/\\D/g,'').slice(0,11);
      if(d.length<=10) return d.replace(/^(\\d{2})(\\d{4})(\\d{0,4}).*/, '($1) $2-$3').trim();
      return d.replace(/^(\\d{2})(\\d{5})(\\d{0,4}).*/, '($1) $2-$3').trim();
    }

    // ---------- CEP via ViaCEP ----------
    async function buscarCEP(cepRaw){
      const cep = cepRaw.replace(/\\D/g, '');
      if(cep.length !== 8) return;
      const cepInput = document.getElementById('cep');
      cepInput.classList.add('loading-cep');
      try{
        const r = await fetch('https://viacep.com.br/ws/'+cep+'/json/');
        const j = await r.json();
        if(j.erro){ alert('CEP não encontrado.'); return; }
        document.getElementById('endereco').value = j.logradouro || '';
        document.getElementById('bairro').value   = j.bairro || '';
        document.getElementById('municipio').value= j.localidade || '';
        document.getElementById('uf').value       = j.uf || '';
      }catch(e){
        alert('Erro ao buscar CEP. Tente novamente.');
      }finally{
        cepInput.classList.remove('loading-cep');
      }
    }

    // ---------- Dinâmicos (cursos / experiências) ----------
    let cursoCount = 0;
    function addCurso(){
      cursoCount++;
      const wrap = document.getElementById('cursos');
      const idx = cursoCount;
      const el = document.createElement('div');
      el.className = 'conditional-field';
      el.innerHTML = \`
        <div class="form-grid">
          <div class="col-6"><label>Curso</label><input type="text" name="curso[\${idx}][nome]"></div>
          <div class="col-6"><label>Instituição</label><input type="text" name="curso[\${idx}][instituicao]"></div>
          <div class="col-12">
            <div class="checkbox-group">
              <label class="checkbox-option"><input type="checkbox" name="curso[\${idx}][status]" value="cursando"><span class="checkbox-custom"></span>Cursando</label>
              <label class="checkbox-option"><input type="checkbox" name="curso[\${idx}][status]" value="concluido" class="chk-concluido"><span class="checkbox-custom"></span>Concluído</label>
            </div>
            <div class="conditional-field hidden ano-wrap">
              <label>Ano de conclusão</label>
              <input type="number" min="1950" max="2035" name="curso[\${idx}][ano]">
            </div>
          </div>
          <div class="col-12" style="display:flex;justify-content:flex-end">
            <button type="button" class="btn btn-danger btn-remover"><i class="fa fa-trash"></i> Remover</button>
          </div>
        </div>\`;
      wrap.appendChild(el);

      el.querySelector('.btn-remover').addEventListener('click', ()=> el.remove());
      // Toggle ano de conclusão quando "Concluído"
      const chk = el.querySelector('.chk-concluido');
      const ano = el.querySelector('.ano-wrap');
      chk.addEventListener('change', ()=> { ano.classList.toggle('hidden', !chk.checked); });
    }

    let xpCount = 0;
    function addXP(){
      xpCount++;
      const wrap = document.getElementById('experiencias');
      const idx = xpCount;
      const el = document.createElement('div');
      el.className = 'conditional-field';
      el.innerHTML = \`
        <div class="form-grid">
          <div class="col-6"><label>Empresa</label><input type="text" name="xp[\${idx}][empresa]"></div>
          <div class="col-6"><label>Cargo</label><input type="text" name="xp[\${idx}][cargo]"></div>
          <div class="col-4"><label>Data de Entrada</label><input type="date" name="xp[\${idx}][entrada]"></div>
          <div class="col-4"><label>Data de Saída</label><input type="date" name="xp[\${idx}][saida]"></div>
          <div class="col-4"><label>Contato (Telefone)</label><input type="tel" name="xp[\${idx}][contato]" placeholder="(00) 00000-0000"></div>
          <div class="col-6"><label>Responsável (Gerente/Líder)</label><input type="text" name="xp[\${idx}][responsavel]"></div>
          <div class="col-12"><label>Principais Atividades</label><textarea name="xp[\${idx}][atividades]" rows="3"></textarea></div>
          <div class="col-12" style="display:flex;justify-content:flex-end">
            <button type="button" class="btn btn-danger btn-remover"><i class="fa fa-trash"></i> Remover</button>
          </div>
        </div>\`;
      wrap.appendChild(el);
      el.querySelector('.btn-remover').addEventListener('click', ()=> el.remove());
    }

    // ---------- Listeners iniciais ----------
    document.addEventListener('DOMContentLoaded', ()=>{
      const cpf = document.getElementById('cpf');
      if(cpf){
        cpf.addEventListener('input', e => {
          const val = formatCPF(e.target.value);
          e.target.value = val;
          if(isCPFFormatted(val)){ e.target.setCustomValidity(''); }
          else { e.target.setCustomValidity('Use o formato 000.000.000-00'); }
        });
      }

      document.getElementById('telefone').addEventListener('input', e => e.target.value = maskPhone(e.target.value));
      document.getElementById('celular').addEventListener('input', e => e.target.value = maskPhone(e.target.value));
      document.getElementById('pretensao').addEventListener('input', e => e.target.value = formatMoneyBR(e.target.value));

      const cepInput = document.getElementById('cep');
      cepInput.addEventListener('blur', ()=> buscarCEP(cepInput.value));

      // Filhos -> mostra "menores de 14" apenas se tiver filhos
      document.querySelectorAll('input[name="possui-filhos"]').forEach(r=>{
        r.addEventListener('change', ()=>{
          const show = document.querySelector('input[name="possui-filhos"][value="sim"]').checked;
          document.getElementById('filhos-extra').classList.toggle('hidden', !show);
        });
      });

      // CNH extra
      document.querySelectorAll('input[name="cnh"]').forEach(r=>{
        r.addEventListener('change', ()=>{
          const show = document.querySelector('input[name="cnh"][value="sim"]').checked;
          document.getElementById('cnh-extra').classList.toggle('hidden', !show);
        });
      });

      // Línguas extra
      document.querySelectorAll('input[name="linguas-estrangeiras"]').forEach(r=>{
        r.addEventListener('change', ()=>{
          const show = document.querySelector('input[name="linguas-estrangeiras"][value="sim"]').checked;
          document.getElementById('linguas-extra').classList.toggle('hidden', !show);
        });
      });

      // Formação: liga/desliga e adiciona 1 bloco ao ativar
      const chkForm = document.getElementById('tem-formacao');
      const formWrap = document.getElementById('formacao-wrap');
      chkForm.addEventListener('change', ()=>{
        formWrap.classList.toggle('hidden', !chkForm.checked);
        if(chkForm.checked && cursoCount===0){ addCurso(); }
      });
      document.getElementById('add-curso').addEventListener('click', addCurso);

      // Experiência: obrigatório escolher uma das opções; abrimos bloco se "sim"
      const xpWrap = document.getElementById('xp-wrap');
      document.querySelectorAll('input[name="tem-experiencia"]').forEach(r=>{
        r.addEventListener('change', ()=>{
          const show = document.querySelector('input[name="tem-experiencia"][value="sim"]').checked;
          xpWrap.classList.toggle('hidden', !show);
          if(show && xpCount===0){ addXP(); }
        });
      });
      document.getElementById('add-xp').addEventListener('click', addXP);
    });

    // ---------- Submit ----------
    document.getElementById('job-form').addEventListener('submit', async (ev)=>{
      ev.preventDefault();
      const form = ev.target;

      // Valida veracidade
      const ver = document.getElementById('veracidade');
      if(!ver.checked){ alert('Você precisa aceitar a Declaração de Veracidade.'); ver.focus(); return; }

      // Validação extra CPF
      const cpfVal = document.getElementById('cpf').value.trim();
      if(!isCPFFormatted(cpfVal)){ alert('CPF inválido. Use o formato 000.000.000-00.'); document.getElementById('cpf').focus(); return; }

      // Constrói payload em x-www-form-urlencoded
      const fd = new FormData(form);
      const data = {};
      fd.forEach((v,k)=>{
        if(data[k] !== undefined){
          if(!Array.isArray(data[k])) data[k] = [data[k]];
          data[k].push(v);
        }else{
          data[k]=v;
        }
      });

      try{
        // Usa no-cors para evitar alerta de erro quando o Apps Script não retorna CORS permitido
        await fetch(form.action, {
          method:'POST',
          mode:'no-cors',
          headers:{ 'Content-Type':'application/x-www-form-urlencoded;charset=UTF-8' },
          body: new URLSearchParams(data).toString()
        });
        alert('Formulário enviado!');
        form.reset();
        // fecha áreas dinâmicas
        document.getElementById('formacao-wrap').classList.add('hidden');
        document.getElementById('cnh-extra').classList.add('hidden');
        document.getElementById('linguas-extra').classList.add('hidden');
        document.getElementById('filhos-extra').classList.add('hidden');
        document.getElementById('cursos').innerHTML=''; cursoCount=0;
        document.getElementById('experiencias').innerHTML=''; xpCount=0;
      }catch(e){
        alert('Não foi possível enviar agora. Tente novamente em instantes.');
      }
    });
  </script>
</body>
</html>

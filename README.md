<!-- INÍCIO DA PARTE 1 -->
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=1024" />
  <title>Formulário de Solicitação de Emprego - Hering Store</title>
  <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet" />
  <style>
/* Reset e configurações básicas */
*{margin:0;padding:0;box-sizing:border-box}
body{font-family:'Segoe UI',Tahoma,Geneva,Verdana,sans-serif;line-height:1.6;color:#333;background:#1a1a1a;min-height:100vh;padding:20px 0}
.container{max-width:1000px;margin:0 auto;padding:0 20px}

/* Header do formulário */
.form-header{background:linear-gradient(135deg,#2c3e50 0%,#34495e 100% );color:#fff;padding:40px 30px;text-align:center;border-radius:15px 15px 0 0;box-shadow:0 4px 20px rgba(0,0,0,.3);position:relative;overflow:hidden}
.form-header::before{content:'';position:absolute;top:-50%;left:-50%;width:200%;height:200%;background:radial-gradient(circle,rgba(255,255,255,.05) 0%,transparent 70%);animation:rotate 30s linear infinite}
@keyframes rotate{from{transform:rotate(0)}to{transform:rotate(360deg)}}
.header-content{position:relative;z-index:1}
.header-icon{font-size:3em;margin-bottom:20px;color:#4CAF50}
.form-header h1{font-size:2.2em;font-weight:700;margin-bottom:10px}
.form-header h2{font-size:1.4em;font-weight:400;margin-bottom:15px;color:#ecf0f1}
.form-header p{font-size:1.1em;opacity:.9;max-width:600px;margin:0 auto}

/* Container do formulário */
.form-container{background:#2a2a2a;border-radius:0 0 15px 15px;box-shadow:0 4px 20px rgba(0,0,0,.3);padding:30px}

/* Blocos do formulário */
.form-block{background:#3a3a3a;border-radius:12px;margin-bottom:25px;box-shadow:0 4px 15px rgba(0,0,0,.2);transition:.3s;border-left:4px solid #4CAF50;animation:slideInUp .6s ease-out forwards;opacity:0;transform:translateY(30px)}
.form-block:hover{transform:translateY(-2px);box-shadow:0 8px 25px rgba(0,0,0,.3)}
.block-header{background:linear-gradient(135deg,#4CAF50 0%,#45a049 100%);color:#fff;padding:20px 25px;border-radius:8px 8px 0 0;display:flex;align-items:center;gap:15px}
.block-header i{font-size:1.5em}
.block-header h3{font-size:1.3em;font-weight:600;margin:0}
.block-content{padding:25px}

/* Grid */
.form-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:20px;align-items:start}
.form-group{display:flex;flex-direction:column}
.form-group.full-width{grid-column:1/-1}
.form-group.large{grid-column:span 2}
.form-group.small{grid-column:span 1;min-width:120px}

/* Labels e Inputs */
label{color:#e0e0e0;font-weight:600;margin-bottom:8px;font-size:.95em}
input[type="text"],input[type="email"],input[type="tel"],input[type="date"],input[type="number"],textarea{background:#4a4a4a;border:2px solid #555;border-radius:8px;padding:12px 15px;color:#e0e0e0;font-size:1em;transition:.3s}
textarea{min-height:90px;resize:vertical}
input:focus,textarea:focus{outline:none;border-color:#4CAF50;box-shadow:0 0 0 3px rgba(76,175,80,.2);background:#5a5a5a}
input:disabled,textarea:disabled{background:#333;color:#888;cursor:not-allowed;opacity:.6}
input::placeholder,textarea::placeholder{color:#999}

/* Radios & Checkboxes customizados */
.radio-group,.checkbox-group{display:flex;gap:20px;flex-wrap:wrap;margin-top:10px}
.radio-option,.checkbox-option{display:flex;align-items:center;gap:10px;cursor:pointer;padding:10px 15px;border-radius:8px;transition:.3s;background:#4a4a4a;border:2px solid #555;color:#e0e0e0;font-weight:500}
.radio-option:hover,.checkbox-option:hover{background:#5a5a5a;border-color:#4CAF50}
.radio-option input[type="radio"],.checkbox-option input[type="checkbox"]{display:none}
.radio-custom{width:20px;height:20px;border:2px solid #777;border-radius:50%;position:relative;transition:.3s}
.radio-option input[type="radio"]:checked + .radio-custom{border-color:#4CAF50;background:#4CAF50}
.radio-option input[type="radio"]:checked + .radio-custom::after{content:'';position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:8px;height:8px;background:#fff;border-radius:50%}
.radio-option input[type="radio"]:checked ~ span:not(.radio-custom){color:#4CAF50}

.checkbox-custom{width:20px;height:20px;border:2px solid #777;border-radius:4px;position:relative;transition:.3s}
.checkbox-option input[type="checkbox"]:checked + .checkbox-custom{border-color:#4CAF50;background:#4CAF50}
.checkbox-option input[type="checkbox"]:checked + .checkbox-custom::after{content:'✓';position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);color:#fff;font-weight:bold;font-size:14px}
.checkbox-option input[type="checkbox"]:checked ~ span:not(.checkbox-custom){color:#4CAF50}

/* Cards específicos */
.course-card,.experience-card{background:#4a4a4a;border:2px solid #555;border-radius:10px;padding:20px;transition:.3s}
.course-card:hover,.experience-card:hover{border-color:#4CAF50;box-shadow:0 5px 15px rgba(0,0,0,.3)}
.course-card h4,.experience-card h4{color:#4CAF50;margin-bottom:15px;font-size:1.1em;display:flex;align-items:center;gap:10px}
.experience-card h4::before{content:'💼';font-size:1.2em}
.education-grid,.experience-container{display:grid;gap:20px}
.hidden-section{display:none}
.hidden-section.show{display:block}

/* Declarações */
.declaration-container{background:#4a4a4a;border:2px solid #555;border-radius:10px;padding:20px;transition:.3s}
.declaration-container:hover{border-color:#4CAF50;box-shadow:0 5px 15px rgba(0,0,0,.3)}
.declaration-text{font-size:.95em;line-height:1.6;color:#e0e0e0;text-align:justify}

/* Seleção de loja (anti-tela) */
#preselect{position:fixed;inset:0;background:rgba(0,0,0,.85);display:flex;align-items:center;justify-content:center;z-index:1000}
.preselect-card{width:min(680px,92vw);background:#2a2a2a;border:2px solid #555;border-radius:14px;box-shadow:0 6px 30px rgba(0,0,0,.5);padding:24px}
.preselect-card h3{color:#fff;margin-bottom:10px}
.preselect-row{display:grid;grid-template-columns:1fr;gap:16px}
.preselect-actions{display:flex;gap:12px;justify-content:flex-end;margin-top:16px}
.badge{display:inline-flex;align-items:center;gap:8px;background:#3a3a3a;border:1px solid #555;color:#e0e0e0;border-radius:999px;padding:6px 12px;font-size:.9em}

/* Botões */
.form-actions{display:flex;gap:20px;justify-content:center;margin-top:40px;padding-top:30px;border-top:2px solid #555}
.btn-submit,.btn-reset,.btn-secondary{display:flex;align-items:center;gap:10px;padding:12px 20px;border:none;border-radius:8px;font-size:1em;font-weight:600;cursor:pointer;transition:.3s;text-transform:uppercase;letter-spacing:1px;position:relative;overflow:hidden}
.btn-submit{background:linear-gradient(135deg,#4CAF50 0%,#45a049 100%);color:#fff;box-shadow:0 4px 15px rgba(76,175,80,.3)}
.btn-reset{background:linear-gradient(135deg,#f44336 0%,#d32f2f 100%);color:#fff;box-shadow:0 4px 15px rgba(244,67,54,.3)}
.btn-secondary{background:#444;color:#fff;border:2px solid #666;text-transform:none;letter-spacing:0}
.btn-submit:hover,.btn-reset:hover,.btn-secondary:hover{transform:translateY(-2px);box-shadow:0 8px 25px rgba(0,0,0,.3)}
.btn-submit:disabled { background: #555; cursor: not-allowed; }

/* Animações / Acessibilidade */
@keyframes slideInUp{to{opacity:1;transform:translateY(0)}}
input:valid{border-color:#4CAF50}
input:invalid:not(:placeholder-shown){border-color:#f44336}
input:focus-visible{outline:2px solid #4CAF50;outline-offset:2px}
::-webkit-scrollbar{width:8px}
::-webkit-scrollbar-track{background:#2a2a2a}
::-webkit-scrollbar-thumb{background:#4CAF50;border-radius:4px}
::-webkit-scrollbar-thumb:hover{background:#45a049}

/* loader CEP */
.loading-cep{position:relative}
.loading-cep::after{content:'';position:absolute;right:10px;top:50%;transform:translateY(-50%);width:16px;height:16px;border:2px solid #4CAF50;border-top:2px solid transparent;border-radius:50%;animation:spin 1s linear infinite}
@keyframes spin{0%{transform:translateY(-50%) rotate(0)}100%{transform:translateY(-50%) rotate(360deg)}}

/* ======= INSERÇÕES PEDIDAS ======= */

/* Anti-tela totalmente opaca */
#preselect { background:#000 !important; }

/* Bloqueia o scroll enquanto a anti-tela estiver ativa */
body.no-scroll { overflow:hidden; }

/* Esconde cabeçalho/rodapé/títulos do tema do GitHub Pages */
.site-header,
.page-header,
.site-footer,
.site-title,
.page-title,
.site-nav,
header[role="banner"],
footer[role="contentinfo"] { display:none !important; }

/* Zera margens/paddings dos wrappers do tema para começar no topo */
main, .page-content, .wrapper { margin:0 !important; padding:0 !important; }

/* Remove qualquer margem/padding do topo da página */
html, body { margin:0; padding:0 !important; }
  </style>
</head>
<body>

  <!-- Anti-tela: escolha Cidade e Filiais -->
  <div id="preselect" role="dialog" aria-modal="true">
    <div class="preselect-card">
      <h3><i class="fas fa-store"></i> Escolha a cidade e filial(is) para sua candidatura</h3>
      <div class="preselect-row">
        <div class="form-group">
          <label for="cidade-select">Cidade *</label>
          <select id="cidade-select" style="background:#4a4a4a;border:2px solid #555;border-radius:8px;padding:12px 15px;color:#e0e0e0">
            <option value="">Selecione...</option>
            <option value="Uberaba">Uberaba</option>
            <option value="Uberlândia">Uberlândia</option>
            <option value="Poços de Caldas">Poços de Caldas</option>
          </select>
        </div>
        <div class="form-group">
          <label>Filial(is) *</label>
          <div id="filiais-box" class="checkbox-group"></div>
        </div>
        <div class="preselect-actions">
          <button type="button" class="btn-secondary" id="btn-cancel-pre">Cancelar</button>
          <button type="button" class="btn-submit" id="btn-continue-pre">Continuar</button>
        </div>
      </div>
    </div>
  </div>

  <div class="container" id="app-root" style="display:none">
    <header class="form-header">
      <div class="header-content">
        <i class="fas fa-briefcase header-icon"></i>
        <h1>FORMULÁRIO DE SOLICITAÇÃO DE EMPREGO</h1>
        <h2>HERING STORE</h2>
        <p>Preencha todos os campos para que sua candidatura seja validada</p>
      </div>
    </header>

    <div class="form-container">
      <!-- Resumo Cidade/Filiais -->
      <div class="form-block">
        <div class="block-header"><i class="fas fa-map-pin"></i><h3>Vaga selecionada</h3></div>
        <div class="block-content">
          <span class="badge"><i class="fas fa-city"></i> <strong id="badge-cidade"></strong></span>
          <span class="badge" style="margin-left:8px"><i class="fas fa-store"></i> <strong id="badge-filiais"></strong></span>
        </div>
      </div>

      <form id="job-application-form" class="job-form" action="https://script.google.com/macros/s/AKfycbzdMkDG0N6xwF_px9n2N2gqqGFjYyv0D_8jOtremC3WSFQBy57_tHwtBg8CEsf-G93N/exec" method="POST">
        <!-- ocultos -->
        <input type="hidden" name="cidade" id="cidade-hidden" />
        <input type="hidden" name="filiais" id="filiais-hidden" />

        <!-- 1. Dados Pessoais -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-user"></i><h3>Dados Pessoais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group full-width">
                <label for="nome-completo">Nome Completo *</label>
                <input type="text" id="nome-completo" name="nome-completo" required />
              </div>
              <div class="form-group">
                <label for="data-nascimento">Data de Nascimento *</label>
                <input type="date" id="data-nascimento" name="data-nascimento" required />
              </div>
              <div class="form-group">
                <label for="rg">RG *</label>
                <input type="text" id="rg" name="rg" required />
              </div>
              <div class="form-group">
                <label for="orgao-emissor">Órgão Emissor *</label>
                <input type="text" id="orgao-emissor" name="orgao-emissor" required />
              </div>
              <div class="form-group">
                <label for="cpf">CPF *</label>
                <input type="text" id="cpf" name="cpf" placeholder="000.000.000-00" required />
              </div>
              <div class="form-group">
                <label for="naturalidade">Naturalidade *</label>
                <input type="text" id="naturalidade" name="naturalidade" required />
              </div>
              <div class="form-group">
                <label for="uf-naturalidade">UF *</label>
                <input type="text" id="uf-naturalidade" name="uf-naturalidade" maxlength="2" required />
              </div>

              <!-- FOTO (name=foto ) -->
              <div class="form-group full-width">
                <label for="foto">Foto do candidato (JPG/PNG, até 5 MB)</label>
                <input type="file" id="foto" name="foto" accept="image/*" />
                <div id="preview-foto" style="display:none;margin-top:10px">
                  <img id="preview-foto-img" alt="Prévia" style="max-width:220px;border-radius:10px;border:2px solid #555"/>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 2. Endereço -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-map-marker-alt"></i><h3>Endereço</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group">
                <label for="cep">CEP *</label>
                <input type="text" id="cep" name="cep" placeholder="00000-000" required onblur="buscarCEP()" />
              </div>
              <div class="form-group large">
                <label for="endereco">Endereço *</label>
                <input type="text" id="endereco" name="endereco" required readonly />
              </div>
              <div class="form-group small">
                <label for="numero">Nº *</label>
                <input type="text" id="numero" name="numero" required />
              </div>
              <div class="form-group">
                <label for="bairro">Bairro *</label>
                <input type="text" id="bairro" name="bairro" required readonly />
              </div>
              <div class="form-group">
                <label for="municipio">Município *</label>
                <input type="text" id="municipio" name="municipio" required readonly />
              </div>
              <div class="form-group small">
                <label for="uf">UF *</label>
                <input type="text" id="uf" name="uf" maxlength="2" required readonly />
              </div>
            </div>
          </div>
        </div>

        <!-- 3. Contatos -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-phone"></i><h3>Contatos Pessoais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group">
                <label for="telefone">Telefone</label>
                <input type="tel" id="telefone" name="telefone" placeholder="(00) 0000-0000" />
              </div>
              <div class="form-group">
                <label for="celular">Celular *</label>
                <input type="tel" id="celular" name="celular" placeholder="(00) 00000-0000" required />
              </div>
              <div class="form-group full-width">
                <label for="email">E-mail *</label>
                <input type="email" id="email" name="email" required />
              </div>
            </div>
          </div>
        </div>

        <!-- 4. Informações Familiares -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-users"></i><h3>Informações Familiares</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group">
                <label for="nome-pai">Nome do Pai</label>
                <input type="text" id="nome-pai" name="nome-pai" />
              </div>
              <div class="form-group">
                <label for="nome-mae">Nome da Mãe *</label>
                <input type="text" id="nome-mae" name="nome-mae" required />
              </div>

              <div class="form-group full-width">
                <label>Estado Civil *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="estado-civil" value="casado" required /><span class="radio-custom"></span>Casado(a)</label>
                  <label class="radio-option"><input type="radio" name="estado-civil" value="solteiro" required /><span class="radio-custom"></span>Solteiro(a)</label>
                  <label class="radio-option"><input type="radio" name="estado-civil" value="divorciado" required /><span class="radio-custom"></span>Divorciado(a)</label>
                </div>
              </div>

              <div class="form-group full-width">
                <label>Residência *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="residencia" value="propria" required /><span class="radio-custom"></span>Própria</label>
                  <label class="radio-option"><input type="radio" name="residencia" value="alugada" required /><span class="radio-custom"></span>Alugada</label>
                </div>
              </div>

              <!-- Fluxo filhos -->
              <div class="form-group full-width">
                <label>Possui Filhos?</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="possui-filhos" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="possui-filhos" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>

                <div class="conditional-field" id="menores-14-container" style="display:none;margin-top:10px">
                  <label>Possui filhos menores de 14 anos?</label>
                  <div class="radio-group">
                    <label class="radio-option"><input type="radio" name="menores-14" value="sim" /><span class="radio-custom"></span>Sim</label>
                    <label class="radio-option"><input type="radio" name="menores-14" value="nao" /><span class="radio-custom"></span>Não</label>
                  </div>
                </div>

                <div class="conditional-field" id="qtd-menores-14-container" style="display:none;margin-top:10px">
                  <label for="qtd-menores-14">Quantidade de filhos menores de 14 anos</label>
                  <input type="number" id="qtd-menores-14" name="qtd-menores-14" min="0" disabled />
                </div>
              </div>

            </div>
          </div>
          <!-- INÍCIO DA PARTE 2 -->
        <!-- 5. Escolaridade -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-graduation-cap"></i><h3>Grau de Escolaridade</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group full-width">
                <label>Selecione seu nível de escolaridade *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="escolaridade" value="fundamental-completo" required /><span class="radio-custom"></span>Fundamental Completo</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="fundamental-incompleto" required /><span class="radio-custom"></span>Fundamental Incompleto</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="medio-completo" required /><span class="radio-custom"></span>Médio Completo</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="medio-incompleto" required /><span class="radio-custom"></span>Médio Incompleto</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="superior-completo" required /><span class="radio-custom"></span>Superior Completo</label>
                  <label class="radio-option"><input type="radio" name="escolaridade" value="superior-incompleto" required /><span class="radio-custom"></span>Superior Incompleto</label>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 6. Formação Acadêmica (dinâmico) -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-certificate"></i><h3>Formação Acadêmica</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group full-width">
                <label class="checkbox-option">
                  <input type="checkbox" id="possui-formacao" name="possui-formacao" onchange="toggleFormacaoAcademica()" />
                  <span class="checkbox-custom"></span>
                  Possuo formação acadêmica
                </label>
              </div>
            </div>

            <div class="hidden-section" id="formacao-academica-section">
              <div class="education-grid">
                <div class="course-container" id="course-container"></div>
              </div>
              <div style="margin-top:15px;display:flex;gap:10px;flex-wrap:wrap">
                <button type="button" class="btn-secondary" id="btn-add-curso" onclick="adicionarCurso()">Adicionar curso</button>
                <button type="button" class="btn-secondary" id="btn-remover-curso" onclick="removerUltimoCurso()">Remover último</button>
              </div>
            </div>
          </div>
        </div>

        <!-- 7. Informações Adicionais -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-info-circle"></i><h3>Informações Adicionais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group">
                <label for="titulo-eleitor">Título de Eleitor nº</label>
                <input type="text" id="titulo-eleitor" name="titulo-eleitor" />
              </div>
              <div class="form-group">
                <label for="zona">Zona</label>
                <input type="text" id="zona" name="zona" />
              </div>

              <div class="form-group full-width">
                <label>Condução Própria</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="conducao-propria" value="sim" /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="conducao-propria" value="nao" /><span class="radio-custom"></span>Não</label>
                </div>
                <div id="vale-transporte-container" class="conditional-field" style="display:none;margin-top:10px">
                  <label>Precisará de vale-transporte?</label>
                  <div class="radio-group">
                    <label class="radio-option"><input type="radio" name="precisa-vale-transporte" value="sim" /><span class="radio-custom"></span>Sim</label>
                    <label class="radio-option"><input type="radio" name="precisa-vale-transporte" value="nao" /><span class="radio-custom"></span>Não</label>
                  </div>
                </div>
              </div>

              <div class="form-group full-width">
                <label>Conhecimento de Informática</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="informatica" value="basico" /><span class="radio-custom"></span>Básico</label>
                  <label class="radio-option"><input type="radio" name="informatica" value="intermediario" /><span class="radio-custom"></span>Intermediário</label>
                  <label class="radio-option"><input type="radio" name="informatica" value="avancado" /><span class="radio-custom"></span>Avançado</label>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 8. Experiências Profissionais -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-history"></i><h3>Experiências Profissionais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group full-width">
                <label>Você possui experiência profissional? *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="tem-experiencia" value="sim" required onchange="toggleExperienciaProfissional()" /><span class="radio-custom"></span>Possuo experiência profissional</label>
                  <label class="radio-option"><input type="radio" name="tem-experiencia" value="nao" required onchange="toggleExperienciaProfissional()" /><span class="radio-custom"></span>Não possuo experiência profissional</label>
                </div>
              </div>
            </div>

            <div class="hidden-section" id="experiencia-profissional-section">
              <div class="experience-container" id="experience-container"></div>

              <div style="margin-top:15px;display:flex;gap:10px;flex-wrap:wrap">
                <button type="button" class="btn-secondary" onclick="adicionarExperiencia()">Adicionar experiência</button>
                <button type="button" class="btn-secondary" onclick="removerUltimaExperiencia()">Remover última</button>
              </div>
            </div>
          </div>
        </div>
        <div class="form-block">
          <div class="block-header"><i class="fas fa-clipboard-check"></i><h3>Informações Finais</h3></div>
          <div class="block-content">
            <div class="form-grid">
              <div class="form-group">
                <label for="pretensao-salarial">Pretensão Salarial</label>
                <input type="text" id="pretensao-salarial" name="pretensao-salarial" placeholder="R$ 0.000,00" />
              </div>
              <div class="form-group">
                <label for="pretensao-cargo">Pretensão de Cargo</label>
                <input type="text" id="pretensao-cargo" name="pretensao-cargo" placeholder="Ex.: Vendedor, Caixa, Estoquista..." />
              </div>

              <div class="form-group full-width">
                <label>Disponibilidade para início imediato *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="disponibilidade-inicio" value="sim" required /><span class="radio-custom"></span>Sim</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-inicio" value="nao" required /><span class="radio-custom"></span>Não</label>
                </div>
              </div>

              <div class="form-group full-width">
                <label>Disponibilidade de Horário *</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="manha" required /><span class="radio-custom"></span>Manhã</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="tarde" required /><span class="radio-custom"></span>Tarde</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="noite" required /><span class="radio-custom"></span>Noite</label>
                  <label class="radio-option"><input type="radio" name="disponibilidade-horario" value="integral" required /><span class="radio-custom"></span>Integral</label>
                </div>
              </div>

              <div class="form-group full-width">
                <label>Como soube da vaga?</label>
                <div class="radio-group">
                  <label class="radio-option"><input type="radio" name="como-soube" value="site" /><span class="radio-custom"></span>Site de Empregos</label>
                  <label class="radio-option"><input type="radio" name="como-soube" value="indicacao" /><span class="radio-custom"></span>Indicação</label>
                  <label class="radio-option"><input type="radio" name="como-soube" value="redes-sociais" /><span class="radio-custom"></span>Redes Sociais</label>
                  <label class="radio-option"><input type="radio" name="como-soube" value="outro" /><span class="radio-custom"></span>Outro</label>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- 10-A. Declaração de Veracidade -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-file-signature"></i><h3>Declaração de Veracidade</h3></div>
          <div class="block-content">
            <div class="declaration-container">
              <label class="checkbox-option" style="background:transparent;border:none;padding:0">
                <input type="checkbox" id="declaracao-veracidade" name="declaracao-veracidade" />
                <span class="checkbox-custom"></span>
                <span class="declaration-text">Declaro, para os devidos fins, que as informações prestadas neste formulário são verdadeiras e completas.</span>
              </label>
            </div>
          </div>
        </div>

        <!-- 10-B. Declaração de Confidencialidade -->
        <div class="form-block">
          <div class="block-header"><i class="fas fa-shield-alt"></i><h3>Declaração de Confidencialidade</h3></div>
          <div class="block-content">
            <div class="declaration-container">
              <p class="declaration-text">
                A Hering Store se compromete a tratar seus dados pessoais com confidencialidade e segurança, utilizando-os exclusivamente para análise
                desta candidatura e processos seletivos relacionados. As informações não serão compartilhadas com terceiros não autorizados e serão
                armazenadas pelo período necessário ao processo, em conformidade com a legislação aplicável (LGPD).
              </p>
            </div>
          </div>
        </div>

        <!-- Ações -->
        <div class="form-actions">
          <button type="submit" class="btn-submit"><i class="fas fa-paper-plane"></i> Enviar Candidatura</button>
          <button type="reset" class="btn-reset"><i class="fas fa-eraser"></i> Limpar Formulário</button>
        </div>

      </form>
    </div>
  </div>

<script>
/* ====== Mapa de filiais por cidade ====== */
const FILIAIS = {
  "Uberaba": ["Hering - Prudente de Morais","Hering - Shopping Uberaba"],
  "Uberlândia": ["Hering - Floriano Peixoto","Hering - Uberlândia Shopping"],
  "Poços de Caldas": ["Hering - Rio de Janeiro"]
};

/* ====== CEP ====== */
async function buscarCEP(){
  const cepInput=document.getElementById('cep');
  const enderecoInput=document.getElementById('endereco');
  const bairroInput=document.getElementById('bairro');
  const municipioInput=document.getElementById('municipio');
  const ufInput=document.getElementById('uf');
  const cep=cepInput.value.replace(/\D/g,'');
  if(cep.length!==8) return;
  cepInput.classList.add('loading-cep');
  try{
    const resp=await fetch(`https://viacep.com.br/ws/${cep}/json/` );
    const data=await resp.json();
    if(data.erro){
      alert('CEP não encontrado.');enderecoInput.value='';bairroInput.value='';municipioInput.value='';ufInput.value='';
    }else{
      enderecoInput.value=data.logradouro||'';bairroInput.value=data.bairro||'';municipioInput.value=data.localidade||'';ufInput.value=data.uf||'';
    }
  }catch(e){console.error(e);alert('Erro ao buscar CEP.');}
  finally{cepInput.classList.remove('loading-cep');}
}

/* ===== Fluxo de filhos ===== */
(function(){
  const rPossui = document.querySelectorAll('input[name="possui-filhos"]');
  const rMenores = document.querySelectorAll('input[name="menores-14"]');
  const contMenores = document.getElementById('menores-14-container');
  const contQtd = document.getElementById('qtd-menores-14-container');
  const inpQtd = document.getElementById('qtd-menores-14');

  function refresh(){
    const possui = document.querySelector('input[name="possui-filhos"]:checked')?.value;
    const menores = document.querySelector('input[name="menores-14"]:checked')?.value;

    if (possui === 'sim') {
      contMenores.style.display = 'block';
      if (menores === 'sim') {
        contQtd.style.display = 'block';
        inpQtd.disabled = false;
      } else {
        contQtd.style.display = 'none';
        inpQtd.disabled = true; inpQtd.value = '';
      }
    } else {
      contMenores.style.display = 'none';
      rMenores.forEach(r=> r.checked=false);
      contQtd.style.display = 'none';
      inpQtd.disabled = true; inpQtd.value = '';
    }
  }
  rPossui.forEach(r=> r.addEventListener('change', refresh));
  rMenores.forEach(r=> r.addEventListener('change', refresh));
  refresh();
})();

/* ===== Condução -> Vale-transporte ===== */
(function(){
  const radios = document.querySelectorAll('input[name="conducao-propria"]');
  const vt = document.getElementById('vale-transporte-container');
  function refresh(){
    const v = document.querySelector('input[name="conducao-propria"]:checked')?.value;
    if (v === 'nao') vt.style.display = 'block';
    else {
      vt.style.display = 'none';
      document.querySelectorAll('input[name="precisa-vale-transporte"]').forEach(r=> r.checked=false);
    }
  }
  radios.forEach(r=> r.addEventListener('change', refresh));
  refresh();
})();

/* ===== Foto: preview e validação (id=foto) ===== */
(function(){
  const fotoInput = document.getElementById('foto');
  if (!fotoInput) return;
  fotoInput.addEventListener('change', () => {
    const file = fotoInput.files?.[0];
    const wrap = document.getElementById('preview-foto');
    const img  = document.getElementById('preview-foto-img');
    if (!file) { wrap.style.display='none'; img.src=''; return; }
    if (!/^image\//.test(file.type)) { alert('Envie uma imagem (JPG/PNG).'); fotoInput.value=''; return; }
    if (file.size > 5*1024*1024) { alert('Tamanho máximo: 5 MB.'); fotoInput.value=''; return; }
    const reader = new FileReader();
    reader.onload = e => { img.src = e.target.result; wrap.style.display = 'block'; };
    reader.readAsDataURL(file);
  });
})();

/* ===== Formação Acadêmica Dinâmica ===== */
let cursoCount=0;
function cursoCardTemplate(idx){
  return `
  <div class="course-card" data-curso="${idx}">
    <h4>Curso ${idx}</h4>
    <div class="form-grid">
      <div class="form-group"><label for="curso${idx}">Curso</label><input type="text" id="curso${idx}" name="curso${idx}"></div>
      <div class="form-group"><label for="instituicao${idx}">Instituição</label><input type="text" id="instituicao${idx}" name="instituicao${idx}"></div>
      <div class="form-group full-width">
        <div class="checkbox-group">
          <label class="checkbox-option"><input type="checkbox" name="status-curso${idx}" value="cursando" onchange="toggleConclusao(${idx})"><span class="checkbox-custom"></span>Cursando</label>
          <label class="checkbox-option"><input type="checkbox" name="status-curso${idx}" value="concluido" onchange="toggleConclusao(${idx})"><span class="checkbox-custom"></span>Concluído</label>
        </div>
        <div class="conditional-field" id="ano-conclusao${idx}-container" style="display:none">
          <label for="ano-conclusao${idx}">Ano de conclusão</label>
          <input type="number" id="ano-conclusao${idx}" name="ano-conclusao${idx}" min="1950" max="2030" disabled>
        </div>
      </div>
    </div>
  </div>`;
}
function adicionarCurso(){ cursoCount++; document.getElementById('course-container').insertAdjacentHTML('beforeend', cursoCardTemplate(cursoCount)); }
function removerUltimoCurso(){ const ctn=document.getElementById('course-container'); if(ctn.lastElementChild){ctn.removeChild(ctn.lastElementChild);cursoCount=Math.max(0,cursoCount-1);} }
function toggleFormacaoAcademica(){ const chk=document.getElementById('possui-formacao'); const sec=document.getElementById('formacao-academica-section'); if(chk.checked){ sec.classList.add('show'); if(cursoCount===0) adicionarCurso(); } else { sec.classList.remove('show'); } }
function toggleConclusao(idx){ const concluido=document.querySelector(`input[name="status-curso${idx}"][value="concluido"]`); const wrap=document.getElementById(`ano-conclusao${idx}-container`); const input=document.getElementById(`ano-conclusao${idx}`); if(concluido && concluido.checked){wrap.style.display='block';input.disabled=false;} else {wrap.style.display='none';input.disabled=true;input.value='';} }

/* ===== Experiências Dinâmicas ===== */
function experienciaCardTemplate(idx){
  return `
  <div class="experience-card" data-exp="${idx}">
    <h4>Experiência ${idx}</h4>
    <div class="form-grid">
      <div class="form-group"><label for="empresa${idx}">Empresa</label><input type="text" id="empresa${idx}" name="empresa${idx}"></div>
      <div class="form-group"><label for="cargo${idx}">Cargo</label><input type="text" id="cargo${idx}" name="cargo${idx}"></div>
      <div class="form-group"><label for="periodo${idx}">Período (meses/anos)</label><input type="text" id="periodo${idx}" name="periodo${idx}" placeholder="Ex.: 1 ano e 6 meses"></div>
      <div class="form-group"><label for="responsavel${idx}">Responsável (gestor/líder)</label><input type="text" id="responsavel${idx}" name="responsavel${idx}"></div>
      <div class="form-group"><label for="contato${idx}">Contato do responsável</label><input type="tel" id="contato${idx}" name="contato${idx}" placeholder="(00) 00000-0000"></div>
      <div class="form-group full-width"><label for="atividades${idx}">Principais Atividades</label><textarea id="atividades${idx}" name="atividades${idx}" rows="3"></textarea></div>
    </div>
  </div>`;
}
function adicionarExperiencia(){ const ctn=document.getElementById('experience-container'); const idx=ctn.children.length+1; ctn.insertAdjacentHTML('beforeend', experienciaCardTemplate(idx)); }
function removerUltimaExperiencia(){ const ctn=document.getElementById('experience-container'); if(ctn.lastElementChild){ctn.removeChild(ctn.lastElementChild);} }
function toggleExperienciaProfissional(){ const tem=document.querySelector('input[name="tem-experiencia"]:checked')?.value; const sec=document.getElementById('experiencia-profissional-section'); if(tem==='sim'){ sec.classList.add('show'); if(!document.querySelector('.experience-card')) adicionarExperiencia(); } else { sec.classList.remove('show'); } }

/* ===== Anti-tela (Cidade/Filiais) ===== */
function initPreselect(){
  document.body.classList.add('no-scroll'); // BLOQUEIA SCROLL ENQUANTO O MODAL ESTÁ ABERTO
  const pre=document.getElementById('preselect');
  const app=document.getElementById('app-root');
  const cidadeSel=document.getElementById('cidade-select');
  const filiaisBox=document.getElementById('filiais-box');
  const btnCancel=document.getElementById('btn-cancel-pre');
  const btnCont=document.getElementById('btn-continue-pre');
  const badgeCidade=document.getElementById('badge-cidade');
  const badgeFiliais=document.getElementById('badge-filiais');
  const inputCidade=document.getElementById('cidade-hidden');
  const inputFiliais=document.getElementById('filiais-hidden');

  function renderFiliais(){
    filiaisBox.innerHTML='';
    const cidade=cidadeSel.value;
    if(!cidade || !FILIAIS[cidade]) return;
    FILIAIS[cidade].forEach((nome)=>{
      filiaisBox.insertAdjacentHTML('beforeend', `
        <label class="checkbox-option">
          <input type="checkbox" value="${nome}">
          <span class="checkbox-custom"></span>${nome}
        </label>
      `);
    });
  }

  cidadeSel.addEventListener('change', renderFiliais);

  btnCancel.addEventListener('click', ()=>{
    cidadeSel.value=''; filiaisBox.innerHTML='';
  });

  btnCont.addEventListener('click', ()=>{
    const cidade=cidadeSel.value;
    if(!cidade){ alert('Selecione a cidade.'); return; }
    const marcadas=[...filiaisBox.querySelectorAll('input[type="checkbox"]:checked')].map(i=>i.value);
    if(!marcadas.length){ alert('Selecione pelo menos uma filial.'); return; }

    badgeCidade.textContent = cidade;
    badgeFiliais.textContent = marcadas.join(', ');
    inputCidade.value = cidade;
    inputFiliais.value = marcadas.join(', ');

    pre.style.display='none';
    app.style.display='block';
    document.body.classList.remove('no-scroll'); // LIBERA O SCROLL
    window.scrollTo(0,0); // GARANTE INÍCIO NO TOPO
  });
}

/* ===== Máscaras e init ===== */
document.addEventListener('DOMContentLoaded', ()=>{
  initPreselect();

  const cpf=document.getElementById('cpf');
  if(cpf){
    cpf.addEventListener('input',e=>{
      let v=e.target.value.replace(/\D/g,'');
      if(v.length>9) v=v.replace(/^(\d{3})(\d{3})(\d{3})(\d{0,2}).*/,'$1.$2.$3-$4');
      else if(v.length>6) v=v.replace(/^(\d{3})(\d{3})(\d{0,3}).*/,'$1.$2.$3');
      else if(v.length>3) v=v.replace(/^(\d{3})(\d{0,3}).*/,'$1.$2');
      e.target.value=v;
    });
  }

  const tel=document.getElementById('telefone');
  if(tel){tel.addEventListener('input',e=>{
    let v=e.target.value.replace(/\D/g,'');
    if(v.length>10) v=v.replace(/^(\d\d)(\d{5})(\d{4}).*/,'($1) $2-$3');
    else if(v.length>6) v=v.replace(/^(\d\d)(\d{4})(\d{0,4}).*/,'($1) $2-$3');
    else if(v.length>2) v=v.replace(/^(\d\d)(\d{0,5})/,'($1) $2');
    e.target.value=v;
  });}

  const cel=document.getElementById('celular');
  if(cel){cel.addEventListener('input',e=>{
    let v=e.target.value.replace(/\D/g,'');
    if(v.length>11) v=v.replace(/^(\d\d)(\d{5})(\d{4}).*/,'($1) $2-$3');
    else if(v.length>7) v=v.replace(/^(\d\d)(\d{5})(\d{0,4}).*/,'($1) $2-$3');
    else if(v.length>2) v=v.replace(/^(\d\d)(\d{0,5})/,'($1) $2');
    e.target.value=v;
  });}

  const pret=document.getElementById('pretensao-salarial');
  if(pret){pret.addEventListener('input',e=>{
    let v=e.target.value.replace(/\D/g,''); v=(parseInt(v||'0',10)/100).toLocaleString('pt-BR',{style:'currency',currency:'BRL'}); e.target.value=v;
  });}
});

/* ===== NOVO ENVIO (com fetch e base64) ===== */
document.getElementById('job-application-form').addEventListener('submit', async function onSubmit(event){
  event.preventDefault(); // Previne o envio padrão do formulário
  const form = event.target;
  const submitButton = form.querySelector('.btn-submit');

  // 1) Valida declaração
  const decl = document.getElementById('declaracao-veracidade');
  if (!decl.checked) {
    alert('Você precisa aceitar a Declaração de Veracidade para prosseguir.');
    decl.scrollIntoView({ behavior: 'smooth', block: 'center' });
    decl.focus();
    return;
  }

  // Desabilita o botão para evitar envios múltiplos
  submitButton.disabled = true;
  submitButton.innerHTML = '<i class="fas fa-spinner fa-spin"></i> Enviando...';

  // 2) Prepara os dados do formulário
  const formData = new FormData(form);

  // 3) Converte cursos e experiências para JSON
  const cursos = [];
  document.querySelectorAll('.course-card').forEach((card, idx) => {
    const i = card.getAttribute('data-curso') || (idx + 1);
    const get = (sel) => (card.querySelector(sel)?.value || '').trim();
    const curso = get(`#curso${i}`) || get('[id^="curso"]');
    const instituicao = get(`#instituicao${i}`) || get('[id^="instituicao"]');
    const status = (card.querySelector(`input[name="status-curso${i}"]:checked`)?.value) || '';
    const ano = get(`#ano-conclusao${i}`) || get('[id^="ano-conclusao"]');
    if (curso || instituicao || status || ano) cursos.push({ curso, instituicao, status, anoConclusao: ano });
  });
  if (cursos.length) {
    formData.append('cursos', JSON.stringify(cursos));
  }

  const temExp = document.querySelector('input[name="tem-experiencia"]:checked')?.value === 'sim';
  if (temExp) {
    const exps = [];
    document.querySelectorAll('.experience-card').forEach((card, idx) => {
      const i = card.getAttribute('data-exp') || (idx + 1);
      const get = (sel) => (card.querySelector(sel)?.value || '').trim();
      const empresa = get(`#empresa${i}`) || get('[id^="empresa"]');
      const cargo = get(`#cargo${i}`) || get('[id^="cargo"]');
      const periodo = get(`#periodo${i}`) || get('[id^="periodo"]');
      const responsavel = get(`#responsavel${i}`) || get('[id^="responsavel"]');
      const contato = get(`#contato${i}`) || get('[id^="contato"]');
      const atividades = get(`#atividades${i}`) || get('[id^="atividades"]');
      if (empresa || cargo || periodo || responsavel || contato || atividades) {
        exps.push({ empresa, cargo, periodo, responsavel, contato, atividades });
      }
    });
    if (exps.length) {
      formData.append('experiencias', JSON.stringify(exps));
    }
  }
  
  // 4) Processa a foto para base64
  const fotoInput = document.getElementById('foto');
  const fotoFile = fotoInput.files?.[0];

  if (fotoFile) {
    try {
      const dataUrl = await new Promise((resolve, reject) => {
        const reader = new FileReader();
        reader.onload = () => resolve(reader.result);
        reader.onerror = reject;
        reader.readAsDataURL(fotoFile);
      });
      formData.append('foto_b64', dataUrl); // Adiciona o base64
    } catch (error) {
      console.error('Erro ao converter a imagem:', error);
      alert('Ocorreu um erro ao processar sua foto. Tente novamente.');
      submitButton.disabled = false;
      submitButton.innerHTML = '<i class="fas fa-paper-plane"></i> Enviar Candidatura';
      return;
    }
  }
  
  // Remove o campo de arquivo para não ser enviado
  formData.delete('foto');

  // 5) Envia os dados usando fetch
  try {
    const response = await fetch(form.action, {
      method: 'POST',
      body: new URLSearchParams(formData) // Envia como x-www-form-urlencoded
    });

    const result = await response.json();

    if (result.success) {
      alert('Candidatura enviada com sucesso!');
      form.reset();
      document.getElementById('preview-foto').style.display = 'none';
      document.getElementById('preview-foto-img').src = '';
      // Opcional: recarregar a página ou redirecionar
      window.location.reload();
    } else {
      throw new Error(result.message || 'Erro desconhecido no servidor.');
    }
  } catch (error) {
    console.error('Erro ao enviar o formulário:', error);
    alert(`Ocorreu um erro ao enviar sua candidatura: ${error.message}. Por favor, tente novamente.`);
  } finally {
    // Reabilita o botão
    submitButton.disabled = false;
    submitButton.innerHTML = '<i class="fas fa-paper-plane"></i> Enviar Candidatura';
  }
});
</script>
</body>
</html>

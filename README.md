<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário de Solicitação de Emprego - Usina Irmãos Afonso</title>
    <link rel="stylesheet" href="styles_v2.css">
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
</head>
<body>
    <div class="container">
        <header class="form-header">
            <div class="header-content">
                <i class="fas fa-briefcase header-icon"></i>
                <h1>FORMULÁRIO DE SOLICITAÇÃO DE EMPREGO</h1>
                <h2>USINA IRMÃOS AFONSO</h2>
                <p>Preencha todos os campos para que sua candidatura seja validada</p>
            </div>
        </header>

        <div class="form-container">
            <form id="job-application-form" class="job-form">
                
                <!-- Bloco 1: Dados Pessoais -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-user"></i>
                        <h3>Dados Pessoais</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group full-width">
                                <label for="nome-completo">Nome Completo *</label>
                                <input type="text" id="nome-completo" name="nome-completo" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="data-nascimento">Data de Nascimento *</label>
                                <input type="date" id="data-nascimento" name="data-nascimento" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="rg">RG *</label>
                                <input type="text" id="rg" name="rg" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="orgao-emissor">Órgão Emissor *</label>
                                <input type="text" id="orgao-emissor" name="orgao-emissor" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="cpf">CPF *</label>
                                <input type="text" id="cpf" name="cpf" pattern="\d{3}\.\d{3}\.\d{3}-\d{2}" placeholder="000.000.000-00" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="naturalidade">Naturalidade *</label>
                                <input type="text" id="naturalidade" name="naturalidade" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="uf-naturalidade">UF *</label>
                                <input type="text" id="uf-naturalidade" name="uf-naturalidade" maxlength="2" required>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 2: Endereço -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-map-marker-alt"></i>
                        <h3>Endereço</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group large">
                                <label for="endereco">Endereço *</label>
                                <input type="text" id="endereco" name="endereco" required>
                            </div>
                            
                            <div class="form-group small">
                                <label for="numero">Nº *</label>
                                <input type="text" id="numero" name="numero" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="bairro">Bairro *</label>
                                <input type="text" id="bairro" name="bairro" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="municipio">Município *</label>
                                <input type="text" id="municipio" name="municipio" required>
                            </div>
                            
                            <div class="form-group small">
                                <label for="uf">UF *</label>
                                <input type="text" id="uf" name="uf" maxlength="2" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="cep">CEP *</label>
                                <input type="text" id="cep" name="cep" pattern="\d{5}-\d{3}" placeholder="00000-000" required>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 3: Contatos -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-phone"></i>
                        <h3>Contatos</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group">
                                <label for="telefone">Telefone</label>
                                <input type="tel" id="telefone" name="telefone" placeholder="(00) 0000-0000">
                            </div>
                            
                            <div class="form-group">
                                <label for="celular">Celular *</label>
                                <input type="tel" id="celular" name="celular" placeholder="(00) 00000-0000" required>
                            </div>
                            
                            <div class="form-group full-width">
                                <label for="email">E-mail *</label>
                                <input type="email" id="email" name="email" required>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 4: Informações Familiares -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-users"></i>
                        <h3>Informações Familiares</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group">
                                <label for="nome-pai">Nome do Pai</label>
                                <input type="text" id="nome-pai" name="nome-pai">
                            </div>
                            
                            <div class="form-group">
                                <label for="nome-mae">Nome da Mãe *</label>
                                <input type="text" id="nome-mae" name="nome-mae" required>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Estado Civil *</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="estado-civil" value="casado" required>
                                        <span class="radio-custom"></span>
                                        Casado(a)
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="estado-civil" value="solteiro" required>
                                        <span class="radio-custom"></span>
                                        Solteiro(a)
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="estado-civil" value="divorciado" required>
                                        <span class="radio-custom"></span>
                                        Divorciado(a)
                                    </label>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Residência *</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="residencia" value="propria" required>
                                        <span class="radio-custom"></span>
                                        Própria
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="residencia" value="alugada" required>
                                        <span class="radio-custom"></span>
                                        Alugada
                                    </label>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Possui Filhos?</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="possui-filhos" value="sim" onchange="toggleFilhosQuantidade()">
                                        <span class="radio-custom"></span>
                                        Sim
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="possui-filhos" value="nao" onchange="toggleFilhosQuantidade()">
                                        <span class="radio-custom"></span>
                                        Não
                                    </label>
                                </div>
                                <div class="conditional-field" id="quantidade-filhos-container" style="display: none;">
                                    <label for="quantidade-filhos">Quantos filhos?</label>
                                    <input type="number" id="quantidade-filhos" name="quantidade-filhos" min="0" disabled>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Menores de 14 anos:</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="menores-14" value="sim">
                                        <span class="radio-custom"></span>
                                        Sim
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="menores-14" value="nao">
                                        <span class="radio-custom"></span>
                                        Não
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 5: Escolaridade -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-graduation-cap"></i>
                        <h3>Grau de Escolaridade</h3>
                    </div>
                    <div class="block-content">
                        <div class="education-grid">
                            <div class="education-card">
                                <h4><i class="fas fa-school"></i> Ensino Fundamental</h4>
                                <div class="checkbox-group">
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="fundamental" value="completo">
                                        <span class="checkbox-custom"></span>
                                        Completo
                                    </label>
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="fundamental" value="incompleto">
                                        <span class="checkbox-custom"></span>
                                        Incompleto
                                    </label>
                                </div>
                            </div>
                            
                            <div class="education-card">
                                <h4><i class="fas fa-book"></i> Ensino Médio</h4>
                                <div class="checkbox-group">
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="medio" value="completo">
                                        <span class="checkbox-custom"></span>
                                        Completo
                                    </label>
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="medio" value="incompleto">
                                        <span class="checkbox-custom"></span>
                                        Incompleto
                                    </label>
                                </div>
                            </div>
                            
                            <div class="education-card">
                                <h4><i class="fas fa-university"></i> Superior</h4>
                                <div class="checkbox-group">
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="superior" value="completo">
                                        <span class="checkbox-custom"></span>
                                        Completo
                                    </label>
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="superior" value="incompleto">
                                        <span class="checkbox-custom"></span>
                                        Incompleto
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 6: Formação Acadêmica -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-certificate"></i>
                        <h3>Formação Acadêmica</h3>
                    </div>
                    <div class="block-content">
                        <div class="course-container">
                            <div class="course-card">
                                <h4>Curso 1</h4>
                                <div class="form-grid">
                                    <div class="form-group">
                                        <label for="curso1">Curso</label>
                                        <input type="text" id="curso1" name="curso1">
                                    </div>
                                    <div class="form-group">
                                        <label for="instituicao1">Instituição</label>
                                        <input type="text" id="instituicao1" name="instituicao1">
                                    </div>
                                    <div class="form-group full-width">
                                        <div class="checkbox-group">
                                            <label class="checkbox-option">
                                                <input type="checkbox" name="status-curso1" value="cursando" onchange="toggleConclusao(1)">
                                                <span class="checkbox-custom"></span>
                                                Cursando
                                            </label>
                                            <label class="checkbox-option">
                                                <input type="checkbox" name="status-curso1" value="concluido" onchange="toggleConclusao(1)">
                                                <span class="checkbox-custom"></span>
                                                Concluído
                                            </label>
                                        </div>
                                        <div class="conditional-field" id="ano-conclusao1-container" style="display: none;">
                                            <label for="ano-conclusao1">Ano de conclusão</label>
                                            <input type="number" id="ano-conclusao1" name="ano-conclusao1" min="1950" max="2030" disabled>
                                        </div>
                                    </div>
                                </div>
                            </div>
                            
                            <div class="course-card">
                                <h4>Curso 2</h4>
                                <div class="form-grid">
                                    <div class="form-group">
                                        <label for="curso2">Curso</label>
                                        <input type="text" id="curso2" name="curso2">
                                    </div>
                                    <div class="form-group">
                                        <label for="instituicao2">Instituição</label>
                                        <input type="text" id="instituicao2" name="instituicao2">
                                    </div>
                                    <div class="form-group full-width">
                                        <div class="checkbox-group">
                                            <label class="checkbox-option">
                                                <input type="checkbox" name="status-curso2" value="cursando" onchange="toggleConclusao(2)">
                                                <span class="checkbox-custom"></span>
                                                Cursando
                                            </label>
                                            <label class="checkbox-option">
                                                <input type="checkbox" name="status-curso2" value="concluido" onchange="toggleConclusao(2)">
                                                <span class="checkbox-custom"></span>
                                                Concluído
                                            </label>
                                        </div>
                                        <div class="conditional-field" id="ano-conclusao2-container" style="display: none;">
                                            <label for="ano-conclusao2">Ano de conclusão</label>
                                            <input type="number" id="ano-conclusao2" name="ano-conclusao2" min="1950" max="2030" disabled>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 7: Informações Adicionais -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-info-circle"></i>
                        <h3>Informações Adicionais</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group">
                                <label for="titulo-eleitor">Título de Eleitor nº</label>
                                <input type="text" id="titulo-eleitor" name="titulo-eleitor">
                            </div>
                            
                            <div class="form-group">
                                <label for="zona">Zona</label>
                                <input type="text" id="zona" name="zona">
                            </div>
                            
                            <div class="form-group full-width">
                                <label>CNH</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="cnh" value="sim" onchange="toggleCNHCategoria()">
                                        <span class="radio-custom"></span>
                                        Sim
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="cnh" value="nao" onchange="toggleCNHCategoria()">
                                        <span class="radio-custom"></span>
                                        Não
                                    </label>
                                </div>
                                <div class="conditional-field" id="categoria-cnh-container" style="display: none;">
                                    <label for="categoria-cnh">Categoria</label>
                                    <input type="text" id="categoria-cnh" name="categoria-cnh" disabled>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Condução Própria</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="conducao-propria" value="sim">
                                        <span class="radio-custom"></span>
                                        Sim
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="conducao-propria" value="nao">
                                        <span class="radio-custom"></span>
                                        Não
                                    </label>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Possui alguma deficiência</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="deficiencia" value="sim">
                                        <span class="radio-custom"></span>
                                        Sim
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="deficiencia" value="nao">
                                        <span class="radio-custom"></span>
                                        Não
                                    </label>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Línguas estrangeiras</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="linguas-estrangeiras" value="sim" onchange="toggleLinguas()">
                                        <span class="radio-custom"></span>
                                        Sim
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="linguas-estrangeiras" value="nao" onchange="toggleLinguas()">
                                        <span class="radio-custom"></span>
                                        Não
                                    </label>
                                </div>
                                <div class="conditional-field" id="quais-linguas-container" style="display: none;">
                                    <label for="quais-linguas">Quais línguas?</label>
                                    <input type="text" id="quais-linguas" name="quais-linguas" disabled>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Conhecimento de Informática</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="informatica" value="basico">
                                        <span class="radio-custom"></span>
                                        Básico
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="informatica" value="intermediario">
                                        <span class="radio-custom"></span>
                                        Intermediário
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="informatica" value="avancado">
                                        <span class="radio-custom"></span>
                                        Avançado
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Botões de Ação -->
                <div class="form-actions">
                    <button type="submit" class="btn-submit">
                        <i class="fas fa-paper-plane"></i>
                        Enviar Candidatura
                    </button>
                    <button type="reset" class="btn-reset">
                        <i class="fas fa-redo"></i>
                        Limpar Formulário
                    </button>
                </div>
            </form>
        </div>
    </div>

    <script>
        function toggleFilhosQuantidade() {
            const possuiFilhos = document.querySelector('input[name="possui-filhos"]:checked');
            const container = document.getElementById('quantidade-filhos-container');
            const input = document.getElementById('quantidade-filhos');
            
            if (possuiFilhos && possuiFilhos.value === 'sim') {
                container.style.display = 'block';
                input.disabled = false;
                input.required = true;
            } else {
                container.style.display = 'none';
                input.disabled = true;
                input.required = false;
                input.value = '';
            }
        }

        function toggleCNHCategoria() {
            const cnh = document.querySelector('input[name="cnh"]:checked');
            const container = document.getElementById('categoria-cnh-container');
            const input = document.getElementById('categoria-cnh');
            
            if (cnh && cnh.value === 'sim') {
                container.style.display = 'block';
                input.disabled = false;
                input.required = true;
            } else {
                container.style.display = 'none';
                input.disabled = true;
                input.required = false;
                input.value = '';
            }
        }

        function toggleLinguas() {
            const linguas = document.querySelector('input[name="linguas-estrangeiras"]:checked');
            const container = document.getElementById('quais-linguas-container');
            const input = document.getElementById('quais-linguas');
            
            if (linguas && linguas.value === 'sim') {
                container.style.display = 'block';
                input.disabled = false;
                input.required = true;
            } else {
                container.style.display = 'none';
                input.disabled = true;
                input.required = false;
                input.value = '';
            }
        }

        function toggleConclusao(courseNumber) {
            const statusInputs = document.querySelectorAll(`input[name="status-curso${courseNumber}"]`);
            const container = document.getElementById(`ano-conclusao${courseNumber}-container`);
            const input = document.getElementById(`ano-conclusao${courseNumber}`);
            
            let showContainer = false;
            statusInputs.forEach(inputEl => {
                if (inputEl.checked && inputEl.value === 'concluido') {
                    showContainer = true;
                }
            });
            
            if (showContainer) {
                container.style.display = 'block';
                input.disabled = false;
                input.required = true;
            } else {
                container.style.display = 'none';
                input.disabled = true;
                input.required = false;
                input.value = '';
            }
        }

        // Prevent multiple selections in education checkboxes
        document.querySelectorAll('input[name="fundamental"], input[name="medio"], input[name="superior"]').forEach(checkbox => {
            checkbox.addEventListener('change', function() {
                if (this.checked) {
                    document.querySelectorAll(`input[name="${this.name}"]`).forEach(other => {
                        if (other !== this) other.checked = false;
                    });
                }
            });
        });

        // Prevent multiple selections in course status checkboxes
        document.querySelectorAll('input[name="status-curso1"], input[name="status-curso2"]').forEach(checkbox => {
            checkbox.addEventListener('change', function() {
                if (this.checked) {
                    document.querySelectorAll(`input[name="${this.name}"]`).forEach(other => {
                        if (other !== this) other.checked = false;
                    });
                }
            });
        });
    </script>
</body>
</html>


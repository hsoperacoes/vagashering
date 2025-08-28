<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário de Solicitação de Emprego - Usina Irmãos Afonso</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <header class="form-header">
            <h1>FORMULÁRIO DE SOLICITAÇÃO DE EMPREGO</h1>
            <h2>USINA IRMÃOS AFONSO</h2>
            <p>Preencha todos os campos abaixo para que sua candidatura seja validada. Este formulário é disponibilizado no site da empresa e também na versão impressa.</p>
        </header>

        <form id="job-application-form" class="job-form">
            <!-- Dados Pessoais -->
            <section class="form-section">
                <h3>Dados Pessoais</h3>
                
                <div class="form-row">
                    <div class="form-group full-width">
                        <label for="nome-completo">Nome Completo:</label>
                        <input type="text" id="nome-completo" name="nome-completo" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="data-nascimento">Data de Nascimento:</label>
                        <input type="date" id="data-nascimento" name="data-nascimento" required>
                    </div>
                    <div class="form-group">
                        <label for="rg">RG:</label>
                        <input type="text" id="rg" name="rg" required>
                    </div>
                    <div class="form-group">
                        <label for="orgao-emissor">Órgão Emissor:</label>
                        <input type="text" id="orgao-emissor" name="orgao-emissor" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="cpf">CPF:</label>
                        <input type="text" id="cpf" name="cpf" pattern="\d{3}\.\d{3}\.\d{3}-\d{2}" placeholder="000.000.000-00" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group large">
                        <label for="endereco">Endereço:</label>
                        <input type="text" id="endereco" name="endereco" required>
                    </div>
                    <div class="form-group small">
                        <label for="numero">Nº:</label>
                        <input type="text" id="numero" name="numero" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="bairro">Bairro:</label>
                        <input type="text" id="bairro" name="bairro" required>
                    </div>
                    <div class="form-group">
                        <label for="municipio">Município:</label>
                        <input type="text" id="municipio" name="municipio" required>
                    </div>
                    <div class="form-group small">
                        <label for="uf">UF:</label>
                        <input type="text" id="uf" name="uf" maxlength="2" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="cep">CEP:</label>
                        <input type="text" id="cep" name="cep" pattern="\d{5}-\d{3}" placeholder="00000-000" required>
                    </div>
                    <div class="form-group">
                        <label for="naturalidade">Naturalidade:</label>
                        <input type="text" id="naturalidade" name="naturalidade" required>
                    </div>
                    <div class="form-group small">
                        <label for="uf-naturalidade">UF:</label>
                        <input type="text" id="uf-naturalidade" name="uf-naturalidade" maxlength="2" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="telefone">Telefone:</label>
                        <input type="tel" id="telefone" name="telefone" placeholder="(00) 0000-0000">
                    </div>
                    <div class="form-group">
                        <label for="celular">Celular:</label>
                        <input type="tel" id="celular" name="celular" placeholder="(00) 00000-0000" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group full-width">
                        <label for="email">E-mail:</label>
                        <input type="email" id="email" name="email" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label for="nome-pai">Nome do Pai:</label>
                        <input type="text" id="nome-pai" name="nome-pai">
                    </div>
                    <div class="form-group">
                        <label for="nome-mae">Nome da Mãe:</label>
                        <input type="text" id="nome-mae" name="nome-mae" required>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Estado Civil:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="estado-civil" value="casado" required>
                                Casado(a)
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="estado-civil" value="solteiro" required>
                                Solteiro(a)
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="estado-civil" value="divorciado" required>
                                Divorciado(a)
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Residência:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="residencia" value="propria" required>
                                Própria
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="residencia" value="alugada" required>
                                Alugada
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Possui Filhos?</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="possui-filhos" value="sim" onchange="toggleFilhosQuantidade()">
                                Sim, quantos:
                            </label>
                            <input type="number" id="quantidade-filhos" name="quantidade-filhos" min="0" disabled>
                            <label class="radio-label">
                                <input type="radio" name="possui-filhos" value="nao" onchange="toggleFilhosQuantidade()">
                                Não
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Menores de 14 anos:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="menores-14" value="sim">
                                Sim
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="menores-14" value="nao">
                                Não
                            </label>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Grau de Escolaridade -->
            <section class="form-section">
                <h3>Grau de Escolaridade</h3>
                
                <div class="education-grid">
                    <div class="education-level">
                        <h4>Ensino Fundamental</h4>
                        <div class="checkbox-group">
                            <label class="checkbox-label">
                                <input type="checkbox" name="fundamental" value="completo">
                                Completo
                            </label>
                            <label class="checkbox-label">
                                <input type="checkbox" name="fundamental" value="incompleto">
                                Incompleto
                            </label>
                        </div>
                    </div>

                    <div class="education-level">
                        <h4>Ensino Médio</h4>
                        <div class="checkbox-group">
                            <label class="checkbox-label">
                                <input type="checkbox" name="medio" value="completo">
                                Completo
                            </label>
                            <label class="checkbox-label">
                                <input type="checkbox" name="medio" value="incompleto">
                                Incompleto
                            </label>
                        </div>
                    </div>

                    <div class="education-level">
                        <h4>Superior</h4>
                        <div class="checkbox-group">
                            <label class="checkbox-label">
                                <input type="checkbox" name="superior" value="completo">
                                Completo
                            </label>
                            <label class="checkbox-label">
                                <input type="checkbox" name="superior" value="incompleto">
                                Incompleto
                            </label>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Formação Acadêmica -->
            <section class="form-section">
                <h3>Formação Acadêmica</h3>
                
                <div class="academic-course">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="curso1">Curso:</label>
                            <input type="text" id="curso1" name="curso1">
                        </div>
                        <div class="form-group">
                            <label for="instituicao1">Instituição:</label>
                            <input type="text" id="instituicao1" name="instituicao1">
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <div class="checkbox-group">
                                <label class="checkbox-label">
                                    <input type="checkbox" name="status-curso1" value="cursando" onchange="toggleConclusao(1)">
                                    Cursando
                                </label>
                                <label class="checkbox-label">
                                    <input type="checkbox" name="status-curso1" value="concluido" onchange="toggleConclusao(1)">
                                    Concluído, ano de conclusão:
                                </label>
                                <input type="number" id="ano-conclusao1" name="ano-conclusao1" min="1950" max="2030" disabled>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="academic-course">
                    <div class="form-row">
                        <div class="form-group">
                            <label for="curso2">Curso:</label>
                            <input type="text" id="curso2" name="curso2">
                        </div>
                        <div class="form-group">
                            <label for="instituicao2">Instituição:</label>
                            <input type="text" id="instituicao2" name="instituicao2">
                        </div>
                    </div>
                    <div class="form-row">
                        <div class="form-group">
                            <div class="checkbox-group">
                                <label class="checkbox-label">
                                    <input type="checkbox" name="status-curso2" value="cursando" onchange="toggleConclusao(2)">
                                    Cursando
                                </label>
                                <label class="checkbox-label">
                                    <input type="checkbox" name="status-curso2" value="concluido" onchange="toggleConclusao(2)">
                                    Concluído, ano de conclusão:
                                </label>
                                <input type="number" id="ano-conclusao2" name="ano-conclusao2" min="1950" max="2030" disabled>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Informações Adicionais -->
            <section class="form-section">
                <h3>Informações Adicionais</h3>
                
                <div class="form-row">
                    <div class="form-group">
                        <label for="titulo-eleitor">Título de Eleitor nº:</label>
                        <input type="text" id="titulo-eleitor" name="titulo-eleitor">
                    </div>
                    <div class="form-group">
                        <label for="zona">Zona:</label>
                        <input type="text" id="zona" name="zona">
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>CNH:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="cnh" value="sim" onchange="toggleCNHCategoria()">
                                Sim, categoria:
                            </label>
                            <input type="text" id="categoria-cnh" name="categoria-cnh" disabled>
                            <label class="radio-label">
                                <input type="radio" name="cnh" value="nao" onchange="toggleCNHCategoria()">
                                Não
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Condução Própria:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="conducao-propria" value="sim">
                                Sim
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="conducao-propria" value="nao">
                                Não
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Possui alguma deficiência:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="deficiencia" value="sim">
                                Sim
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="deficiencia" value="nao">
                                Não
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Línguas estrangeiras:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="linguas-estrangeiras" value="sim" onchange="toggleLinguas()">
                                Sim, quais:
                            </label>
                            <input type="text" id="quais-linguas" name="quais-linguas" disabled>
                            <label class="radio-label">
                                <input type="radio" name="linguas-estrangeiras" value="nao" onchange="toggleLinguas()">
                                Não
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-row">
                    <div class="form-group">
                        <label>Conhecimento de Informática:</label>
                        <div class="radio-group">
                            <label class="radio-label">
                                <input type="radio" name="informatica" value="basico">
                                Básico
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="informatica" value="intermediario">
                                Intermediário
                            </label>
                            <label class="radio-label">
                                <input type="radio" name="informatica" value="avancado">
                                Avançado
                            </label>
                        </div>
                    </div>
                </div>
            </section>

            <div class="form-actions">
                <button type="submit" class="submit-btn">Enviar Candidatura</button>
                <button type="reset" class="reset-btn">Limpar Formulário</button>
            </div>
        </form>
    </div>

    <script>
        function toggleFilhosQuantidade() {
            const possuiFilhos = document.querySelector('input[name="possui-filhos"]:checked');
            const quantidadeInput = document.getElementById('quantidade-filhos');
            
            if (possuiFilhos && possuiFilhos.value === 'sim') {
                quantidadeInput.disabled = false;
                quantidadeInput.required = true;
            } else {
                quantidadeInput.disabled = true;
                quantidadeInput.required = false;
                quantidadeInput.value = '';
            }
        }

        function toggleCNHCategoria() {
            const cnh = document.querySelector('input[name="cnh"]:checked');
            const categoriaInput = document.getElementById('categoria-cnh');
            
            if (cnh && cnh.value === 'sim') {
                categoriaInput.disabled = false;
                categoriaInput.required = true;
            } else {
                categoriaInput.disabled = true;
                categoriaInput.required = false;
                categoriaInput.value = '';
            }
        }

        function toggleLinguas() {
            const linguas = document.querySelector('input[name="linguas-estrangeiras"]:checked');
            const linguasInput = document.getElementById('quais-linguas');
            
            if (linguas && linguas.value === 'sim') {
                linguasInput.disabled = false;
                linguasInput.required = true;
            } else {
                linguasInput.disabled = true;
                linguasInput.required = false;
                linguasInput.value = '';
            }
        }

        function toggleConclusao(courseNumber) {
            const statusInputs = document.querySelectorAll(`input[name="status-curso${courseNumber}"]`);
            const anoInput = document.getElementById(`ano-conclusao${courseNumber}`);
            
            statusInputs.forEach(input => {
                if (input.checked && input.value === 'concluido') {
                    anoInput.disabled = false;
                    anoInput.required = true;
                } else if (input.checked && input.value === 'cursando') {
                    anoInput.disabled = true;
                    anoInput.required = false;
                    anoInput.value = '';
                }
            });
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


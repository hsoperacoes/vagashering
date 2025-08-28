<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Formulário de Solicitação de Emprego - Hering Store</title>
    <style>
/* Reset e configurações básicas */
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    line-height: 1.6;
    color: #333;
    background: #1a1a1a;
    min-height: 100vh;
    padding: 20px 0;
}

.container {
    max-width: 1000px;
    margin: 0 auto;
    padding: 0 20px;
}

/* Header do formulário */
.form-header {
    background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
    color: white;
    padding: 40px 30px;
    text-align: center;
    border-radius: 15px 15px 0 0;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
    position: relative;
    overflow: hidden;
}

.form-header::before {
    content: '';
    position: absolute;
    top: -50%;
    left: -50%;
    width: 200%;
    height: 200%;
    background: radial-gradient(circle, rgba(255,255,255,0.05) 0%, transparent 70%);
    animation: rotate 30s linear infinite;
}

@keyframes rotate {
    from { transform: rotate(0deg); }
    to { transform: rotate(360deg); }
}

.header-content {
    position: relative;
    z-index: 1;
}

.header-icon {
    font-size: 3em;
    margin-bottom: 20px;
    color: #4CAF50;
}

.form-header h1 {
    font-size: 2.2em;
    font-weight: 700;
    margin-bottom: 10px;
}

.form-header h2 {
    font-size: 1.4em;
    font-weight: 400;
    margin-bottom: 15px;
    color: #ecf0f1;
}

.form-header p {
    font-size: 1.1em;
    opacity: 0.9;
    max-width: 600px;
    margin: 0 auto;
}

/* Container do formulário */
.form-container {
    background: #2a2a2a;
    border-radius: 0 0 15px 15px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
    padding: 30px;
}

/* Blocos do formulário */
.form-block {
    background: #3a3a3a;
    border-radius: 12px;
    margin-bottom: 25px;
    box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
    transition: all 0.3s ease;
    border-left: 4px solid #4CAF50;
}

.form-block:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(0, 0, 0, 0.3);
}

.block-header {
    background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
    color: white;
    padding: 20px 25px;
    border-radius: 8px 8px 0 0;
    display: flex;
    align-items: center;
    gap: 15px;
}

.block-header i {
    font-size: 1.5em;
}

.block-header h3 {
    font-size: 1.3em;
    font-weight: 600;
    margin: 0;
}

.block-content {
    padding: 25px;
}

/* Grid do formulário */
.form-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
    gap: 20px;
    align-items: start;
}

.form-group {
    display: flex;
    flex-direction: column;
}

.form-group.full-width {
    grid-column: 1 / -1;
}

.form-group.large {
    grid-column: span 2;
}

.form-group.small {
    grid-column: span 1;
    min-width: 120px;
}

/* Labels */
label {
    color: #e0e0e0;
    font-weight: 600;
    margin-bottom: 8px;
    font-size: 0.95em;
}

/* Inputs */
input[type="text"],
input[type="email"],
input[type="tel"],
input[type="date"],
input[type="number"] {
    background: #4a4a4a;
    border: 2px solid #555;
    border-radius: 8px;
    padding: 12px 15px;
    color: #e0e0e0;
    font-size: 1em;
    transition: all 0.3s ease;
}

input[type="text"]:focus,
input[type="email"]:focus,
input[type="tel"]:focus,
input[type="date"]:focus,
input[type="number"]:focus {
    outline: none;
    border-color: #4CAF50;
    box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
    background: #5a5a5a;
}

input:disabled {
    background: #333;
    color: #888;
    cursor: not-allowed;
    opacity: 0.6;
}

input::placeholder {
    color: #999;
}

/* Radio buttons customizados */
.radio-group {
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    margin-top: 10px;
}

.radio-option {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    padding: 10px 15px;
    border-radius: 8px;
    transition: all 0.3s ease;
    background: #4a4a4a;
    border: 2px solid #555;
    color: #e0e0e0;
    font-weight: 500;
}

.radio-option:hover {
    background: #5a5a5a;
    border-color: #4CAF50;
}

.radio-option input[type="radio"] {
    display: none;
}

.radio-custom {
    width: 20px;
    height: 20px;
    border: 2px solid #777;
    border-radius: 50%;
    position: relative;
    transition: all 0.3s ease;
}

.radio-option input[type="radio"]:checked + .radio-custom {
    border-color: #4CAF50;
    background: #4CAF50;
}

.radio-option input[type="radio"]:checked + .radio-custom::after {
    content: '';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    width: 8px;
    height: 8px;
    background: white;
    border-radius: 50%;
}

.radio-option input[type="radio"]:checked ~ span:not(.radio-custom) {
    color: #4CAF50;
}

/* Checkboxes customizados */
.checkbox-group {
    display: flex;
    gap: 15px;
    flex-wrap: wrap;
    margin-top: 10px;
}

.checkbox-option {
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    padding: 10px 15px;
    border-radius: 8px;
    transition: all 0.3s ease;
    background: #4a4a4a;
    border: 2px solid #555;
    color: #e0e0e0;
    font-weight: 500;
}

.checkbox-option:hover {
    background: #5a5a5a;
    border-color: #4CAF50;
}

.checkbox-option input[type="checkbox"] {
    display: none;
}

.checkbox-custom {
    width: 20px;
    height: 20px;
    border: 2px solid #777;
    border-radius: 4px;
    position: relative;
    transition: all 0.3s ease;
}

.checkbox-option input[type="checkbox"]:checked + .checkbox-custom {
    border-color: #4CAF50;
    background: #4CAF50;
}

.checkbox-option input[type="checkbox"]:checked + .checkbox-custom::after {
    content: '✓';
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    color: white;
    font-weight: bold;
    font-size: 14px;
}

.checkbox-option input[type="checkbox"]:checked ~ span:not(.checkbox-custom) {
    color: #4CAF50;
}

/* Grid de educação */
.education-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
    gap: 20px;
}

.education-card {
    background: #4a4a4a;
    border: 2px solid #555;
    border-radius: 10px;
    padding: 20px;
    transition: all 0.3s ease;
}

.education-card:hover {
    border-color: #4CAF50;
    transform: translateY(-2px);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.education-card h4 {
    color: #4CAF50;
    margin-bottom: 15px;
    font-size: 1.1em;
    display: flex;
    align-items: center;
    gap: 10px;
}

.education-card .checkbox-group {
    justify-content: center;
    flex-direction: column;
    gap: 10px;
}

/* Container de cursos */
.course-container {
    display: grid;
    gap: 20px;
}

.course-card {
    background: #4a4a4a;
    border: 2px solid #555;
    border-radius: 10px;
    padding: 20px;
    transition: all 0.3s ease;
}

.course-card:hover {
    border-color: #4CAF50;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.course-card h4 {
    color: #4CAF50;
    margin-bottom: 15px;
    font-size: 1.1em;
}

/* Campos condicionais */
.conditional-field {
    margin-top: 15px;
    padding: 15px;
    background: #3a3a3a;
    border-radius: 8px;
    border-left: 3px solid #4CAF50;
}

.conditional-field label {
    color: #4CAF50;
    font-size: 0.9em;
}

/* Botões de ação */
.form-actions {
    display: flex;
    gap: 20px;
    justify-content: center;
    margin-top: 40px;
    padding-top: 30px;
    border-top: 2px solid #555;
}

.btn-submit,
.btn-reset {
    display: flex;
    align-items: center;
    gap: 10px;
    padding: 15px 30px;
    border: none;
    border-radius: 8px;
    font-size: 1.1em;
    font-weight: 600;
    cursor: pointer;
    transition: all 0.3s ease;
    text-transform: uppercase;
    letter-spacing: 1px;
    position: relative;
    overflow: hidden;
}

.btn-submit {
    background: linear-gradient(135deg, #4CAF50 0%, #45a049 100%);
    color: white;
    box-shadow: 0 4px 15px rgba(76, 175, 80, 0.3);
}

.btn-submit:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(76, 175, 80, 0.4);
    background: linear-gradient(135deg, #45a049 0%, #3d8b40 100%);
}

.btn-reset {
    background: linear-gradient(135deg, #f44336 0%, #d32f2f 100%);
    color: white;
    box-shadow: 0 4px 15px rgba(244, 67, 54, 0.3);
}

.btn-reset:hover {
    transform: translateY(-2px);
    box-shadow: 0 8px 25px rgba(244, 67, 54, 0.4);
    background: linear-gradient(135deg, #d32f2f 0%, #b71c1c 100%);
}

.btn-submit::before,
.btn-reset::before {
    content: '';
    position: absolute;
    top: 0;
    left: -100%;
    width: 100%;
    height: 100%;
    background: linear-gradient(90deg, transparent, rgba(255,255,255,0.2), transparent);
    transition: left 0.5s;
}

.btn-submit:hover::before,
.btn-reset:hover::before {
    left: 100%;
}

/* Responsividade */
@media (max-width: 768px) {
    .container {
        padding: 0 10px;
    }
    
    .form-header {
        padding: 30px 20px;
        border-radius: 10px 10px 0 0;
    }
    
    .form-header h1 {
        font-size: 1.8em;
    }
    
    .form-header h2 {
        font-size: 1.2em;
    }
    
    .form-container {
        padding: 20px;
        border-radius: 0 0 10px 10px;
    }
    
    .form-block {
        margin-bottom: 20px;
    }
    
    .block-header {
        padding: 15px 20px;
    }
    
    .block-content {
        padding: 20px;
    }
    
    .form-grid {
        grid-template-columns: 1fr;
        gap: 15px;
    }
    
    .form-group.large,
    .form-group.small {
        grid-column: 1;
    }
    
    .education-grid {
        grid-template-columns: 1fr;
        gap: 15px;
    }
    
    .radio-group,
    .checkbox-group {
        flex-direction: column;
        gap: 10px;
    }
    
    .form-actions {
        flex-direction: column;
        gap: 15px;
    }
    
    .btn-submit,
    .btn-reset {
        width: 100%;
        justify-content: center;
    }
}

@media (max-width: 480px) {
    body {
        padding: 10px 0;
    }
    
    .form-header h1 {
        font-size: 1.5em;
    }
    
    .form-header h2 {
        font-size: 1.1em;
    }
    
    .form-header p {
        font-size: 1em;
    }
    
    .header-icon {
        font-size: 2.5em;
    }
    
    .block-header {
        padding: 12px 15px;
    }
    
    .block-header h3 {
        font-size: 1.1em;
    }
    
    .block-content {
        padding: 15px;
    }
    
    input[type="text"],
    input[type="email"],
    input[type="tel"],
    input[type="date"],
    input[type="number"] {
        padding: 10px 12px;
    }
}

/* Animações de entrada */
.form-block {
    animation: slideInUp 0.6s ease-out forwards;
    opacity: 0;
    transform: translateY(30px);
}

.form-block:nth-child(1) { animation-delay: 0.1s; }
.form-block:nth-child(2) { animation-delay: 0.2s; }
.form-block:nth-child(3) { animation-delay: 0.3s; }
.form-block:nth-child(4) { animation-delay: 0.4s; }
.form-block:nth-child(5) { animation-delay: 0.5s; }
.form-block:nth-child(6) { animation-delay: 0.6s; }
.form-block:nth-child(7) { animation-delay: 0.7s; }

@keyframes slideInUp {
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Estados de validação */
input:valid {
    border-color: #4CAF50;
}

input:invalid:not(:placeholder-shown) {
    border-color: #f44336;
}

/* Melhorias de acessibilidade */
input:focus-visible {
    outline: 2px solid #4CAF50;
    outline-offset: 2px;
}

.radio-option:focus-within,
.checkbox-option:focus-within {
    background: #5a5a5a;
    border-color: #4CAF50;
    outline: 2px solid #4CAF50;
    outline-offset: 2px;
}

/* Scrollbar personalizada */
::-webkit-scrollbar {
    width: 8px;
}

::-webkit-scrollbar-track {
    background: #2a2a2a;
}

::-webkit-scrollbar-thumb {
    background: #4CAF50;
    border-radius: 4px;
}

::-webkit-scrollbar-thumb:hover {
    background: #45a049;
}

/* Container de experiências */
.experience-container {
    display: grid;
    gap: 25px;
}

.experience-card {
    background: #4a4a4a;
    border: 2px solid #555;
    border-radius: 10px;
    padding: 20px;
    transition: all 0.3s ease;
}

.experience-card:hover {
    border-color: #4CAF50;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.experience-card h4 {
    color: #4CAF50;
    margin-bottom: 15px;
    font-size: 1.1em;
    display: flex;
    align-items: center;
    gap: 10px;
}

.experience-card h4::before {
    content: '💼';
    font-size: 1.2em;
}

/* Container de declaração */
.declaration-container {
    background: #4a4a4a;
    border: 2px solid #555;
    border-radius: 10px;
    padding: 20px;
    transition: all 0.3s ease;
}

.declaration-container:hover {
    border-color: #4CAF50;
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
}

.declaration-checkbox {
    align-items: flex-start !important;
    padding: 0 !important;
    background: transparent !important;
    border: none !important;
    margin: 0 !important;
}

.declaration-text {
    font-size: 0.95em;
    line-height: 1.6;
    color: #e0e0e0;
    margin-left: 10px;
    text-align: justify;
}

.declaration-checkbox:hover .declaration-text {
    color: #4CAF50;
}

/* Animações para novos blocos */
.form-block:nth-child(8) { animation-delay: 0.8s; }
.form-block:nth-child(9) { animation-delay: 0.9s; }
.form-block:nth-child(10) { animation-delay: 1.0s; }

/* Máscara para pretensão salarial */
#pretensao-salarial {
    text-align: right;
}

/* Estilos para campos de experiência */
.experience-card .form-grid {
    margin-top: 15px;
}

.experience-card .form-group label {
    color: #b0b0b0;
    font-size: 0.9em;
}

.experience-card input:focus {
    border-color: #4CAF50;
    box-shadow: 0 0 0 3px rgba(76, 175, 80, 0.2);
}

/* Responsividade para experiências */
@media (max-width: 768px) {
    .experience-container {
        gap: 20px;
    }
    
    .experience-card {
        padding: 15px;
    }
    
    .experience-card h4 {
        font-size: 1em;
    }
    
    .declaration-container {
        padding: 15px;
    }
    
    .declaration-text {
        font-size: 0.9em;
    }
}

/* Estilos para seções ocultas */
.hidden-section {
    display: none;
    animation: slideInDown 0.5s ease-out forwards;
}

.hidden-section.show {
    display: block;
}

@keyframes slideInDown {
    from {
        opacity: 0;
        transform: translateY(-20px);
    }
    to {
        opacity: 1;
        transform: translateY(0);
    }
}

/* Loading indicator para CEP */
.loading-cep {
    position: relative;
}

.loading-cep::after {
    content: '';
    position: absolute;
    right: 10px;
    top: 50%;
    transform: translateY(-50%);
    width: 16px;
    height: 16px;
    border: 2px solid #4CAF50;
    border-top: 2px solid transparent;
    border-radius: 50%;
    animation: spin 1s linear infinite;
}

@keyframes spin {
    0% { transform: translateY(-50%) rotate(0deg); }
    100% { transform: translateY(-50%) rotate(360deg); }
}
</style>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css" rel="stylesheet">
</head>
<body>
    <div class="container">
        <header class="form-header">
            <div class="header-content">
                <i class="fas fa-briefcase header-icon"></i>
                <h1>FORMULÁRIO DE SOLICITAÇÃO DE EMPREGO</h1>
                <h2>HERING STORE</h2>
                <p>Preencha todos os campos para que sua candidatura seja validada</p>
            </div>
        </header>
        
        <div class="form-container">
            <form id="job-application-form" class="job-form" action="https://script.google.com/macros/s/AKfycbzdMkDG0N6xwF_px9n2N2gqqGFjYyv0D_8jOtremC3WSFQBy57_tHwtBg8CEsf-G93N/exec" method="POST">
                
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
                            <div class="form-group">
                                <label for="cep">CEP *</label>
                                <input type="text" id="cep" name="cep" pattern="\d{5}-?\d{3}" placeholder="00000-000" required onblur="buscarCEP()">
                            </div>
                            
                            <div class="form-group large">
                                <label for="endereco">Endereço *</label>
                                <input type="text" id="endereco" name="endereco" required readonly>
                            </div>
                            
                            <div class="form-group small">
                                <label for="numero">Nº *</label>
                                <input type="text" id="numero" name="numero" required>
                            </div>
                            
                            <div class="form-group">
                                <label for="bairro">Bairro *</label>
                                <input type="text" id="bairro" name="bairro" required readonly>
                            </div>
                            
                            <div class="form-group">
                                <label for="municipio">Município *</label>
                                <input type="text" id="municipio" name="municipio" required readonly>
                            </div>
                            
                            <div class="form-group small">
                                <label for="uf">UF *</label>
                                <input type="text" id="uf" name="uf" maxlength="2" required readonly>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 3: Contatos Pessoais -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-phone"></i>
                        <h3>Contatos Pessoais</h3>
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
                        <div class="form-grid">
                            <div class="form-group full-width">
                                <label>Selecione seu nível de escolaridade *</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="escolaridade" value="fundamental-completo" required>
                                        <span class="radio-custom"></span>
                                        Ensino Fundamental Completo
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="escolaridade" value="fundamental-incompleto" required>
                                        <span class="radio-custom"></span>
                                        Ensino Fundamental Incompleto
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="escolaridade" value="medio-completo" required>
                                        <span class="radio-custom"></span>
                                        Ensino Médio Completo
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="escolaridade" value="medio-incompleto" required>
                                        <span class="radio-custom"></span>
                                        Ensino Médio Incompleto
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="escolaridade" value="superior-completo" required>
                                        <span class="radio-custom"></span>
                                        Ensino Superior Completo
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="escolaridade" value="superior-incompleto" required>
                                        <span class="radio-custom"></span>
                                        Ensino Superior Incompleto
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 6: Formação Acadêmica (Oculto por padrão) -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-certificate"></i>
                        <h3>Formação Acadêmica</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group full-width">
                                <label class="checkbox-option">
                                    <input type="checkbox" id="possui-formacao" name="possui-formacao" onchange="toggleFormacaoAcademica()">
                                    <span class="checkbox-custom"></span>
                                    Possui formação acadêmica (cursos técnicos, superiores, pós-graduação, etc.)
                                </label>
                            </div>
                        </div>
                        
                        <div class="hidden-section" id="formacao-academica-section">
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

                <!-- Bloco 8: Experiências Profissionais -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-history"></i>
                        <h3>Experiências Profissionais</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group full-width">
                                <label class="checkbox-option">
                                    <input type="checkbox" id="possui-experiencia" name="possui-experiencia" onchange="toggleExperienciaProfissional()">
                                    <span class="checkbox-custom"></span>
                                    Possui experiência profissional
                                </label>
                            </div>
                        </div>
                        
                        <div class="hidden-section" id="experiencia-profissional-section">
                            <div class="experience-container">
                                <div class="experience-card">
                                    <h4>Experiência 1</h4>
                                    <div class="form-grid">
                                        <div class="form-group">
                                            <label for="empresa1">Empresa</label>
                                            <input type="text" id="empresa1" name="empresa1">
                                        </div>
                                        <div class="form-group">
                                            <label for="cargo1">Cargo</label>
                                            <input type="text" id="cargo1" name="cargo1">
                                        </div>
                                        <div class="form-group">
                                            <label for="data-entrada1">Data de Entrada</label>
                                            <input type="date" id="data-entrada1" name="data-entrada1">
                                        </div>
                                        <div class="form-group">
                                            <label for="data-saida1">Data de Saída</label>
                                            <input type="date" id="data-saida1" name="data-saida1">
                                        </div>
                                        <div class="form-group full-width">
                                            <label for="atividades1">Principais Atividades</label>
                                            <textarea id="atividades1" name="atividades1" rows="3"></textarea>
                                        </div>
                                    </div>
                                </div>
                                
                                <div class="experience-card">
                                    <h4>Experiência 2</h4>
                                    <div class="form-grid">
                                        <div class="form-group">
                                            <label for="empresa2">Empresa</label>
                                            <input type="text" id="empresa2" name="empresa2">
                                        </div>
                                        <div class="form-group">
                                            <label for="cargo2">Cargo</label>
                                            <input type="text" id="cargo2" name="cargo2">
                                        </div>
                                        <div class="form-group">
                                            <label for="data-entrada2">Data de Entrada</label>
                                            <input type="date" id="data-entrada2" name="data-entrada2">
                                        </div>
                                        <div class="form-group">
                                            <label for="data-saida2">Data de Saída</label>
                                            <input type="date" id="data-saida2" name="data-saida2">
                                        </div>
                                        <div class="form-group full-width">
                                            <label for="atividades2">Principais Atividades</label>
                                            <textarea id="atividades2" name="atividades2" rows="3"></textarea>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 9: Informações Finais -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-clipboard-check"></i>
                        <h3>Informações Finais</h3>
                    </div>
                    <div class="block-content">
                        <div class="form-grid">
                            <div class="form-group">
                                <label for="pretensao-salarial">Pretensão Salarial</label>
                                <input type="text" id="pretensao-salarial" name="pretensao-salarial" placeholder="R$ 0.000,00">
                            </div>
                            
                            <div class="form-group">
                                <label for="disponibilidade-inicio">Disponibilidade para Início</label>
                                <input type="text" id="disponibilidade-inicio" name="disponibilidade-inicio">
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Disponibilidade de Horário</label>
                                <div class="checkbox-group">
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="disponibilidade-horario" value="manha">
                                        <span class="checkbox-custom"></span>
                                        Manhã
                                    </label>
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="disponibilidade-horario" value="tarde">
                                        <span class="checkbox-custom"></span>
                                        Tarde
                                    </label>
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="disponibilidade-horario" value="noite">
                                        <span class="checkbox-custom"></span>
                                        Noite
                                    </label>
                                    <label class="checkbox-option">
                                        <input type="checkbox" name="disponibilidade-horario" value="integral">
                                        <span class="checkbox-custom"></span>
                                        Integral
                                    </label>
                                </div>
                            </div>
                            
                            <div class="form-group full-width">
                                <label>Como soube da vaga?</label>
                                <div class="radio-group">
                                    <label class="radio-option">
                                        <input type="radio" name="como-soube" value="site">
                                        <span class="radio-custom"></span>
                                        Site de Empregos
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="como-soube" value="indicacao">
                                        <span class="radio-custom"></span>
                                        Indicação
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="como-soube" value="redes-sociais">
                                        <span class="radio-custom"></span>
                                        Redes Sociais
                                    </label>
                                    <label class="radio-option">
                                        <input type="radio" name="como-soube" value="outro">
                                        <span class="radio-custom"></span>
                                        Outro
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <!-- Bloco 10: Declaração de Veracidade -->
                <div class="form-block">
                    <div class="block-header">
                        <i class="fas fa-file-signature"></i>
                        <h3>Declaração de Veracidade</h3>
                    </div>
                    <div class="block-content">
                        <div class="declaration-container">
                            <label class="checkbox-option declaration-checkbox">
                                <input type="checkbox" id="declaracao-veracidade" name="declaracao-veracidade" required>
                                <span class="checkbox-custom"></span>
                                <span class="declaration-text">
                                    Declaro para os devidos fins que as informações prestadas neste formulário são verdadeiras e completas, assumindo total responsabilidade pelas mesmas. Estou ciente de que a falsidade das informações poderá implicar na minha desclassificação do processo seletivo, sem prejuízo das demais medidas legais cabíveis.
                                </span>
                            </label>
                        </div>
                    </div>
                </div>

                <div class="form-actions">
                    <button type="submit" class="btn-submit"><i class="fas fa-paper-plane"></i> Enviar Candidatura</button>
                    <button type="reset" class="btn-reset"><i class="fas fa-eraser"></i> Limpar Formulário</button>
                </div>
            </form>
        </div>
    </div>

    <script>
        // Função para buscar CEP
        async function buscarCEP() {
            const cepInput = document.getElementById('cep');
            const enderecoInput = document.getElementById('endereco');
            const bairroInput = document.getElementById('bairro');
            const municipioInput = document.getElementById('municipio');
            const ufInput = document.getElementById('uf');

            const cep = cepInput.value.replace(/\D/g, ''); // Remove caracteres não numéricos

            if (cep.length !== 8) {
                return; // CEP inválido
            }

            cepInput.classList.add('loading-cep');

            try {
                const response = await fetch(`https://viacep.com.br/ws/${cep}/json/`);
                const data = await response.json();

                if (data.erro) {
                    alert('CEP não encontrado.');
                    enderecoInput.value = '';
                    bairroInput.value = '';
                    municipioInput.value = '';
                    ufInput.value = '';
                } else {
                    enderecoInput.value = data.logradouro;
                    bairroInput.value = data.bairro;
                    municipioInput.value = data.localidade;
                    ufInput.value = data.uf;
                }
            } catch (error) {
                console.error('Erro ao buscar CEP:', error);
                alert('Erro ao buscar CEP. Tente novamente.');
            } finally {
                cepInput.classList.remove('loading-cep');
            }
        }

        // Função para alternar campo de quantidade de filhos
        function toggleFilhosQuantidade() {
            const possuiFilhosSim = document.querySelector('input[name="possui-filhos"][value="sim"]');
            const quantidadeFilhosContainer = document.getElementById('quantidade-filhos-container');
            const quantidadeFilhosInput = document.getElementById('quantidade-filhos');

            if (possuiFilhosSim.checked) {
                quantidadeFilhosContainer.style.display = 'block';
                quantidadeFilhosInput.disabled = false;
            } else {
                quantidadeFilhosContainer.style.display = 'none';
                quantidadeFilhosInput.disabled = true;
                quantidadeFilhosInput.value = '';
            }
        }

        // Função para alternar campo de categoria CNH
        function toggleCNHCategoria() {
            const cnhSim = document.querySelector('input[name="cnh"][value="sim"]');
            const categoriaCNHContainer = document.getElementById('categoria-cnh-container');
            const categoriaCNHInput = document.getElementById('categoria-cnh');

            if (cnhSim.checked) {
                categoriaCNHContainer.style.display = 'block';
                categoriaCNHInput.disabled = false;
            } else {
                categoriaCNHContainer.style.display = 'none';
                categoriaCNHInput.disabled = true;
                categoriaCNHInput.value = '';
            }
        }

        // Função para alternar campo de línguas estrangeiras
        function toggleLinguas() {
            const linguasSim = document.querySelector('input[name="linguas-estrangeiras"][value="sim"]');
            const quaisLinguasContainer = document.getElementById('quais-linguas-container');
            const quaisLinguasInput = document.getElementById('quais-linguas');

            if (linguasSim.checked) {
                quaisLinguasContainer.style.display = 'block';
                quaisLinguasInput.disabled = false;
            } else {
                quaisLinguasContainer.style.display = 'none';
                quaisLinguasInput.disabled = true;
                quaisLinguasInput.value = '';
            }
        }

        // Função para alternar seção de formação acadêmica
        function toggleFormacaoAcademica() {
            const possuiFormacao = document.getElementById('possui-formacao');
            const formacaoAcademicaSection = document.getElementById('formacao-academica-section');

            if (possuiFormacao.checked) {
                formacaoAcademicaSection.classList.add('show');
            } else {
                formacaoAcademicaSection.classList.remove('show');
            }
        }

        // Função para alternar campo de ano de conclusão do curso
        function toggleConclusao(cursoNum) {
            const cursando = document.querySelector(`input[name="status-curso${cursoNum}"][value="cursando"]`);
            const concluido = document.querySelector(`input[name="status-curso${cursoNum}"][value="concluido"]`);
            const anoConclusaoContainer = document.getElementById(`ano-conclusao${cursoNum}-container`);
            const anoConclusaoInput = document.getElementById(`ano-conclusao${cursoNum}`);

            if (concluido.checked) {
                anoConclusaoContainer.style.display = 'block';
                anoConclusaoInput.disabled = false;
            } else {
                anoConclusaoContainer.style.display = 'none';
                anoConclusaoInput.disabled = true;
                anoConclusaoInput.value = '';
            }
        }

        // Função para alternar seção de experiência profissional
        function toggleExperienciaProfissional() {
            const possuiExperiencia = document.getElementById('possui-experiencia');
            const experienciaProfissionalSection = document.getElementById('experiencia-profissional-section');

            if (possuiExperiencia.checked) {
                experienciaProfissionalSection.classList.add('show');
            } else {
                experienciaProfissionalSection.classList.remove('show');
            }
        }

        // Inicializar estados dos campos condicionais ao carregar a página
        document.addEventListener('DOMContentLoaded', () => {
            toggleFilhosQuantidade();
            toggleCNHCategoria();
            toggleLinguas();
            toggleFormacaoAcademica();
            toggleExperienciaProfissional();
            toggleConclusao(1);
            toggleConclusao(2);

            // Máscara para CPF
            const cpfInput = document.getElementById('cpf');
            if (cpfInput) {
                cpfInput.addEventListener('input', (e) => {
                    let value = e.target.value.replace(/\D/g, '');
                    if (value.length > 9) {
                        value = value.replace(/^(\d{3})(\d{3})(\d{3})(\d{2})$/, '$1.$2.$3-$4');
                    } else if (value.length > 6) {
                        value = value.replace(/^(\d{3})(\d{3})(\d{3})$/, '$1.$2.$3');
                    } else if (value.length > 3) {
                        value = value.replace(/^(\d{3})(\d{3})$/, '$1.$2');
                    }
                    e.target.value = value;
                });
            }

            // Máscara para Telefone
            const telefoneInput = document.getElementById('telefone');
            if (telefoneInput) {
                telefoneInput.addEventListener('input', (e) => {
                    let value = e.target.value.replace(/\D/g, '');
                    if (value.length > 10) {
                        value = value.replace(/^(\d\d)(\d{5})(\d{4}).*/, '($1) $2-$3');
                    } else if (value.length > 6) {
                        value = value.replace(/^(\d\d)(\d{4})(\d{0,4}).*/, '($1) $2-$3');
                    } else if (value.length > 2) {
                        value = value.replace(/^(\d\d)(\d{0,5})/, '($1) $2');
                    }
                    e.target.value = value;
                });
            }

            // Máscara para Celular
            const celularInput = document.getElementById('celular');
            if (celularInput) {
                celularInput.addEventListener('input', (e) => {
                    let value = e.target.value.replace(/\D/g, '');
                    if (value.length > 11) {
                        value = value.replace(/^(\d\d)(\d{5})(\d{4}).*/, '($1) $2-$3');
                    } else if (value.length > 7) {
                        value = value.replace(/^(\d\d)(\d{5})(\d{0,4}).*/, '($1) $2-$3');
                    } else if (value.length > 2) {
                        value = value.replace(/^(\d\d)(\d{0,5})/, '($1) $2');
                    }
                    e.target.value = value;
                });
            }

            // Máscara para Pretensão Salarial
            const pretensaoSalarialInput = document.getElementById('pretensao-salarial');
            if (pretensaoSalarialInput) {
                pretensaoSalarialInput.addEventListener('input', (e) => {
                    let value = e.target.value.replace(/\D/g, '');
                    value = (parseInt(value, 10) / 100).toLocaleString('pt-BR', { style: 'currency', currency: 'BRL' });
                    e.target.value = value;
                });
            }
        });

        // Adicionar um event listener para o envio do formulário
        document.getElementById('job-application-form').addEventListener('submit', async function(event) {
            event.preventDefault(); // Previne o envio padrão do formulário

            const form = event.target;
            const formData = new FormData(form);
            const data = {};
            formData.forEach((value, key) => {
                // Lidar com múltiplos valores para o mesmo nome (ex: checkboxes)
                if (key === 'disponibilidade-horario') {
                    if (!data[key]) {
                        data[key] = [];
                    }
                    data[key].push(value);
                } else {
                    data[key] = value;
                }
            });

            // Adicionar campos de curso e experiência dinamicamente
            const cursos = [];
            for (let i = 1; i <= 2; i++) { // Assumindo 2 cursos
                const curso = document.getElementById(`curso${i}`).value;
                const instituicao = document.getElementById(`instituicao${i}`).value;
                const statusCurso = document.querySelector(`input[name="status-curso${i}"]:checked`)?.value;
                const anoConclusao = document.getElementById(`ano-conclusao${i}`).value;
                if (curso || instituicao || statusCurso || anoConclusao) {
                    cursos.push({
                        curso: curso,
                        instituicao: instituicao,
                        status: statusCurso,
                        anoConclusao: anoConclusao
                    });
                }
            }
            if (cursos.length > 0) {
                data['cursos'] = cursos;
            }

            const experiencias = [];
            for (let i = 1; i <= 2; i++) { // Assumindo 2 experiências
                const empresa = document.getElementById(`empresa${i}`).value;
                const cargo = document.getElementById(`cargo${i}`).value;
                const dataEntrada = document.getElementById(`data-entrada${i}`).value;
                const dataSaida = document.getElementById(`data-saida${i}`).value;
                const atividades = document.getElementById(`atividades${i}`).value;
                if (empresa || cargo || dataEntrada || dataSaida || atividades) {
                    experiencias.push({
                        empresa: empresa,
                        cargo: cargo,
                        dataEntrada: dataEntrada,
                        dataSaida: dataSaida,
                        atividades: atividades
                    });
                }
            }
            if (experiencias.length > 0) {
                data['experiencias'] = experiencias;
            }

            try {
                const response = await fetch(form.action, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/x-www-form-urlencoded' // ou 'application/json' se o script esperar JSON
                    },
                    body: new URLSearchParams(data).toString() // Envia como form-urlencoded
                });

                if (response.ok) {
                    alert('Formulário enviado com sucesso!');
                    form.reset(); // Limpa o formulário após o envio
                } else {
                    alert('Erro ao enviar o formulário. Tente novamente.');
                }
            } catch (error) {
                console.error('Erro:', error);
                alert('Ocorreu um erro ao enviar o formulário. Verifique sua conexão e tente novamente.');
            }
        });
    </script>
</body>
</html>



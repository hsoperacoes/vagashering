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


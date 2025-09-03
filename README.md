<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Teste envio de foto</title>
  <style>
    body{font-family:system-ui,Segoe UI,Arial;padding:24px;background:#111;color:#eee}
    .card{max-width:520px;margin:auto;background:#1e1e1e;border:1px solid #333;border-radius:12px;padding:20px}
    label{display:block;margin:12px 0 6px}
    input[type="text"],input[type="file"]{width:100%;padding:10px;border-radius:8px;border:1px solid #444;background:#2a2a2a;color:#eee}
    button{margin-top:16px;padding:12px 18px;border:0;border-radius:8px;background:#29a35a;color:#fff;font-weight:600;cursor:pointer}
    #preview{display:none;margin-top:12px}
    #preview img{max-width:180px;border-radius:10px;border:1px solid #444}
    .msg{margin-top:14px}
  </style>
</head>
<body>
  <div class="card">
    <h2>Teste • Enviar foto anexada</h2>

    <form id="f" action="https://script.google.com/macros/s/AKfycbzdMkDG0N6xwF_px9n2N2gqqGFjYyv0D_8jOtremC3WSFQBy57_tHwtBg8CEsf-G93N/exec"
          method="POST" enctype="multipart/form-data" novalidate>
      <label for="nome">Nome</label>
      <input id="nome" name="nome" type="text" required>

      <label for="foto">Foto (JPG ou PNG, até 5MB)</label>
      <input id="foto" name="foto-candidato" type="file" accept="image/jpeg,image/png" required>

      <div id="preview"><img id="previmg" alt="Prévia"></div>

      <button type="submit">Enviar</button>
      <div id="msg" class="msg"></div>
    </form>
  </div>

  <script>
    // Prévia + validação básica de tipo/tamanho
    (function(){
      const inp = document.getElementById('foto');
      const prev = document.getElementById('preview');
      const img  = document.getElementById('previmg');
      inp.addEventListener('change', () => {
        const f = inp.files?.[0];
        if (!f) { prev.style.display='none'; return; }
        if (!/^image\/(jpeg|png)$/i.test(f.type)) { alert('Use JPG ou PNG.'); inp.value=''; prev.style.display='none'; return; }
        if (f.size > 5*1024*1024) { alert('Máximo 5MB.'); inp.value=''; prev.style.display='none'; return; }
        const r = new FileReader();
        r.onload = e => { img.src = e.target.result; prev.style.display='block'; };
        r.readAsDataURL(f);
      });
    })();

    document.getElementById('f').addEventListener('submit', async (ev) => {
      ev.preventDefault();
      const form = ev.target;
      const msg  = document.getElementById('msg');

      // força validação do HTML5
      if (!form.reportValidity()) return;

      // garante que veio arquivo
      const file = document.getElementById('foto').files[0];
      if (!file) { alert('Selecione uma foto.'); return; }

      const fd = new FormData(form);
      msg.textContent = 'Enviando...';

      try {
        const res = await fetch(form.action, { method:'POST', body: fd });
        let payload = null;
        try { payload = await res.json(); } catch(_){}

        if (payload && payload.success === true) {
          msg.textContent = 'OK! Verifique o e-mail — a foto deve estar anexada.';
          form.reset();
          document.getElementById('preview').style.display='none';
        } else if (payload && payload.success === false) {
          msg.textContent = 'Erro: ' + (payload.message || 'Falha no envio.');
        } else if (res.ok) {
          // caiu em no-cors/JSON ilegível, mas o POST foi enviado
          msg.textContent = 'Pode ter enviado, mas não deu pra ler a resposta (CORS). Confira o e-mail.';
        } else {
          msg.textContent = 'Falha no envio. Código HTTP: ' + res.status;
        }
      } catch (e) {
        console.error(e);
        msg.textContent = 'Falha de rede. Veja no Apps Script se registrou o doPost e confira o e-mail.';
      }
    });
  </script>
</body>
</html>

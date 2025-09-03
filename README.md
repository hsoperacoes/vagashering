<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Teste envio de foto (anexo)</title>
  <style>
    body{font-family:system-ui,Segoe UI,Arial;padding:24px;background:#111;color:#eee}
    .card{max-width:520px;margin:auto;background:#1e1e1e;border:1px solid #333;border-radius:12px;padding:20px}
    label{display:block;margin:12px 0 6px}
    input[type="text"],input[type="file"]{width:100%;padding:10px;border-radius:8px;border:1px solid #444;background:#2a2a2a;color:#eee}
    button{margin-top:16px;padding:12px 18px;border:0;border-radius:8px;background:#29a35a;color:#fff;font-weight:600;cursor:pointer}
    #preview{display:none;margin-top:12px}
    #preview img{max-width:200px;border-radius:10px;border:1px solid #444}
    .msg{margin-top:12px;opacity:.9}
  </style>
</head>
<body>
  <div class="card">
    <h2>Teste • Enviar foto anexada</h2>

    <!-- IMPORTANTE: action aponta para seu WebApp -->
    <form id="f" action="https://script.google.com/macros/s/AKfycbzdMkDG0N6xwF_px9n2N2gqqGFjYyv0D_8jOtremC3WSFQBy57_tHwtBg8CEsf-G93N/exec" method="POST">
      <label for="nome">Nome</label>
      <input id="nome" name="nome" type="text" required>

      <label for="foto">Foto (JPG/PNG, até 5MB)</label>
      <input id="foto" type="file" accept="image/jpeg,image/png" required>
      <!-- aqui vamos colocar a imagem em Base64 pra enviar -->
      <input type="hidden" id="foto_b64" name="foto_b64">

      <div id="preview"><img id="previmg" alt="Prévia"></div>

      <button type="submit">Enviar</button>
      <div id="msg" class="msg"></div>
    </form>
  </div>

  <script>
    // Lê arquivo -> Base64 (dataURL) e mostra prévia
    (function(){
      const inp = document.getElementById('foto');
      const hidden = document.getElementById('foto_b64');
      const prevWrap = document.getElementById('preview');
      const prevImg = document.getElementById('previmg');

      inp.addEventListener('change', () => {
        const f = inp.files?.[0];
        hidden.value = '';
        prevWrap.style.display = 'none';
        prevImg.src = '';

        if (!f) return;
        if (!/^image\/(jpeg|png)$/i.test(f.type)) { alert('Use JPG ou PNG.'); inp.value=''; return; }
        if (f.size > 5*1024*1024) { alert('Máximo 5MB.'); inp.value=''; return; }

        const r = new FileReader();
        r.onload = e => {
          hidden.value = e.target.result;     // data:image/...;base64,xxxx
          prevImg.src = e.target.result;
          prevWrap.style.display = 'block';
        };
        r.readAsDataURL(f);
      });
    })();

    // Envia via fetch (para receber resposta bonitinha); se falhar CORS, cai no no-cors
    document.getElementById('f').addEventListener('submit', async (ev) => {
      ev.preventDefault();
      const msg = document.getElementById('msg');
      msg.textContent = 'Enviando...';

      const nome = document.getElementById('nome').value.trim();
      const b64  = document.getElementById('foto_b64').value;

      if (!b64) { msg.textContent = 'Selecione uma foto válida.'; return; }

      try {
        const fd = new FormData();
        fd.append('nome', nome);
        fd.append('foto_b64', b64);

        let res = await fetch(ev.target.action, { method:'POST', body: fd });
        let ok = res.ok, payload = null;
        try { payload = await res.json(); } catch(_){}

        if (ok || (payload && payload.success)) {
          msg.textContent = 'OK! Verifique o e-mail — a foto deve estar anexada.';
          ev.target.reset();
          document.getElementById('preview').style.display='none';
        } else {
          // tenta no-cors (alguns deployments não deixam ler a resposta)
          await fetch(ev.target.action, { method:'POST', mode:'no-cors', body: fd });
          msg.textContent = 'Pode ter enviado. Confira o e-mail (resposta não pôde ser lida por CORS).';
        }
      } catch (e) {
        console.error(e);
        msg.textContent = 'Falha de rede. Mesmo assim, confira o e-mail.';
      }
    });
  </script>
</body>
</html>

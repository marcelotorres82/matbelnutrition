# IMC Atlético — Calculadora para Academia

Widget de cálculo de IMC com contexto esportivo, pronto para embed na Nuvemshop via Vercel.

---

## Deploy na Vercel

### Pré-requisito
- Conta na [Vercel](https://vercel.com) (gratuita)
- [Git](https://git-scm.com) instalado

### Passo a passo

```bash
# 1. Crie um repositório no GitHub e faça push dos arquivos
git init
git add .
git commit -m "IMC Atlético"
git remote add origin https://github.com/SEU_USUARIO/imc-atletico.git
git push -u origin main
```

2. Acesse [vercel.com/new](https://vercel.com/new)
3. Importe o repositório GitHub
4. Clique em **Deploy** — sem configuração extra necessária
5. Anote a URL gerada, ex: `https://imc-atletico.vercel.app`

---

## Integração com a Nuvemshop

### Opção 1 — HTML personalizado em página (recomendado)

1. No painel admin da Nuvemshop, vá em **Conteúdo > Páginas**
2. Crie ou edite uma página
3. Mude o editor para **HTML** (ícone `<>`)
4. Cole o código abaixo, substituindo a URL:

```html
<div style="max-width:460px; margin:0 auto;">
  <iframe
    src="https://imc-atletico.vercel.app"
    width="100%"
    height="640"
    frameborder="0"
    scrolling="no"
    style="border-radius:20px; overflow:hidden;"
    title="Calculadora de IMC Atlético"
  ></iframe>
</div>
```

### Opção 2 — Sidebar ou seção do tema

1. Vá em **Personalizar tema > Editar HTML/CSS**
2. Encontre o arquivo do layout onde quer inserir (ex: `product.html` ou `sidebar.html`)
3. Adicione o mesmo código `<iframe>` acima no local desejado

### Opção 3 — Bloco em qualquer página via JavaScript

Cole no rodapé do seu tema (`layout/theme.html`) antes do `</body>`:

```html
<script>
  // Renderiza o widget em qualquer elemento com id="imc-widget"
  document.addEventListener('DOMContentLoaded', function() {
    var el = document.getElementById('imc-widget');
    if (el) {
      var iframe = document.createElement('iframe');
      iframe.src = 'https://imc-atletico.vercel.app';
      iframe.style = 'width:100%;height:640px;border:none;border-radius:20px;';
      el.appendChild(iframe);
    }
  });
</script>
```

Então em qualquer página HTML da loja, basta adicionar:
```html
<div id="imc-widget"></div>
```

---

## Personalização

| O que mudar | Onde |
|---|---|
| Cores da marca | Variáveis CSS no `:root` (linha ~10) |
| Modalidades esportivas | Array `<select>` no HTML + objeto `notas` no JS |
| Textos de contexto atlético | Objeto `notas` no JavaScript |
| Logo/ícone | Bloco `.header-icon` no HTML |

---

## Estrutura dos arquivos

```
imc-atletico/
├── index.html     ← aplicação completa (HTML + CSS + JS)
├── vercel.json    ← configuração de deploy e headers CORS/iframe
└── README.md      ← este arquivo
```

# Impulso Hub — site institucional

Site de página única (single-page), tema escuro, com duas abas (**Início** e **Contato**).
Posicionamento: hub de tecnologia e serviços com foco em **IA aplicada** a vendas, marketing e cobranças.

## O que tem nesta pasta

- **`index.html`** — o site inteiro, **autossuficiente** (HTML + CSS + JS + fontes inline num único arquivo). Abre direto no navegador e funciona offline. É isto que você publica.

> Observação: este `index.html` foi **gerado/empacotado** a partir de um protótipo. Não edite o `index.html` à mão — ele é minificado. Se precisar mudar conteúdo, peça o arquivo-fonte (`Impulso Hub.dc.html`) ou recrie o site no seu ambiente preferido a partir da descrição abaixo.

## Objetivo deste handoff

**Subir o site no ar** no domínio **impulsohub.com** (já registrado pelo usuário). Por ser um único arquivo estático, qualquer hospedagem de site estático serve. Abaixo, os caminhos mais simples.

---

## Opção A — Cloudflare Pages (recomendado se o DNS já estiver na Cloudflare)

1. Crie um repositório Git com o conteúdo desta pasta (só o `index.html` basta).
2. No painel Cloudflare → **Workers & Pages** → **Create** → **Pages** → conecte o repositório (ou use **Direct Upload** e arraste o `index.html`).
3. Build: **sem build** (framework preset = *None*). Output directory = raiz.
4. Após o deploy, vá em **Custom domains** → adicione `impulsohub.com` e `www.impulsohub.com`.
5. Como o domínio é registrado, aponte o DNS (registros que o Cloudflare indicar — normalmente um CNAME/registro gerenciado automático se o domínio estiver na Cloudflare).

## Opção B — Vercel

1. `npm i -g vercel` (ou use o site da Vercel).
2. Nesta pasta: `vercel` → siga o assistente (sem framework, sem build).
3. No projeto → **Settings → Domains** → adicione `impulsohub.com`.
4. A Vercel mostra os registros DNS a configurar no seu registrador:
   - Apex `impulsohub.com` → registro **A** `76.76.21.21` (ou o que a Vercel indicar)
   - `www` → **CNAME** `cname.vercel-dns.com`

## Opção C — Netlify (drag & drop, mais rápido)

1. Acesse app.netlify.com → **Add new site → Deploy manually**.
2. Arraste esta pasta (`impulso-hub-site`) para a área de upload.
3. **Domain settings → Add custom domain** → `impulsohub.com`.
4. Configure os registros DNS que a Netlify indicar no seu registrador (apex via registro A/ALIAS + `www` via CNAME).

## Opção D — GitHub Pages

1. Crie um repo, suba o `index.html` na raiz (branch `main`).
2. **Settings → Pages** → Source = `main` / root.
3. **Custom domain** → `impulsohub.com` (cria um arquivo `CNAME`).
4. No registrador: registros **A** do GitHub Pages (`185.199.108.153` … `111/110/109/108.153`) para o apex e **CNAME** `ww` → `<usuario>.github.io` para o www.

---

## DNS — resumo

Onde quer que hospede, o padrão é:

| Host | Tipo | Valor |
|------|------|-------|
| `@` (apex / impulsohub.com) | A (ou ALIAS/ANAME) | IP/host que a plataforma indicar |
| `www` | CNAME | host que a plataforma indicar |

Ative **HTTPS** (todas as opções acima emitem certificado automático). Propagação de DNS pode levar de minutos a algumas horas.

## Checklist pós-deploy

- [ ] `https://impulsohub.com` carrega
- [ ] `https://www.impulsohub.com` redireciona para o apex (ou vice-versa)
- [ ] HTTPS ativo (cadeado)
- [ ] Botão **Enviar uma mensagem** (aba Contato) abre o cliente de e-mail
- [ ] Favicon/título — ver "Melhorias opcionais"

## Melhorias opcionais (rápidas)

- **`<title>` e favicon:** o `index.html` empacotado não tem `<title>` próprio nem favicon. Vale adicionar, no `<head>`:
  ```html
  <title>Impulso Hub — Impulsionando crescimento com inteligência</title>
  <meta name="description" content="Hub de tecnologia e serviços com foco em IA aplicada a vendas, marketing e cobranças.">
  <link rel="icon" href="favicon.svg" type="image/svg+xml">
  ```
  (peça o favicon SVG do símbolo "Órbita" — pode ser gerado a partir da identidade.)
- **Open Graph / preview de link:** adicionar `og:title`, `og:description`, `og:image` para compartilhamento bonito no WhatsApp/LinkedIn.

## Contato configurado

O botão da aba **Contato** abre um e-mail (`mailto:`) para o endereço pessoal do dono, com assunto pré-preenchido "Impulso Hub". O endereço não aparece em texto visível na página — só na ação do botão.

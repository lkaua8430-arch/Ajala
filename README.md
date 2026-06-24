# AJALA — Site Standalone

Site completo da AJALA em um único arquivo HTML autocontido.  
Sem build, sem dependências, sem servidor.

---

## Como colocar no ar

### Opção 1 — Vercel (recomendado, grátis)

1. Acesse [vercel.com](https://vercel.com) e crie uma conta
2. Clique em **Add New → Project**
3. Escolha **Upload** e arraste o arquivo `ajala.html`
4. Renomeie para `index.html` se solicitado
5. Clique em **Deploy**

Seu site estará no ar em menos de 1 minuto em um link `*.vercel.app`.  
Para usar domínio próprio (`ajala.com`), configure em **Settings → Domains**.

---

### Opção 2 — Netlify Drop (mais simples ainda)

1. Acesse [app.netlify.com/drop](https://app.netlify.com/drop)
2. Arraste o arquivo `ajala.html` para a área indicada
3. Pronto — link gerado automaticamente

Para domínio próprio: **Site Settings → Domain Management → Add custom domain**.

---

### Opção 3 — GitHub Pages (grátis, com versionamento)

```bash
# 1. Crie um repositório público no GitHub
# 2. Faça upload do arquivo renomeado como index.html
# 3. Vá em Settings → Pages → Branch: main → / (root) → Save
# URL: https://seu-usuario.github.io/ajala
```

---

### Opção 4 — Servidor próprio / VPS

Qualquer servidor web serve o arquivo diretamente:

```bash
# Nginx — coloque o arquivo em:
/var/www/html/index.html

# Apache — mesma coisa:
/var/www/html/index.html

# Ou rode localmente para testar:
python3 -m http.server 3000
# Abra: http://localhost:3000/ajala.html
```

---

## O que está incluso

| Recurso | Status |
|---|---|
| Página Home completa (Hero, Novidades, Editorial, Categorias, Mais Desejados, Newsletter) | ✅ |
| Página Loja com busca, filtros por categoria e ordenação | ✅ |
| Página de produto com galeria, seleção de tamanho/cor e validação | ✅ |
| Carrinho lateral com quantidade, remoção e subtotal | ✅ |
| Persistência do carrinho via `localStorage` | ✅ |
| Menu mobile com animação slide | ✅ |
| Header transparente → sólido no scroll | ✅ |
| Animações: hero zoom, scroll reveal, hover zoom nos produtos, banner parallax | ✅ |
| Página Sobre, Contato, Privacidade, 404 | ✅ |
| Totalmente em Português Brasileiro (pt-BR) | ✅ |
| Responsivo: mobile, tablet e desktop | ✅ |
| 12 produtos com imagens via CDN | ✅ |
| Sem dependências externas (exceto Google Fonts) | ✅ |

---

## O que ainda precisa de integração real

### Checkout e Pagamento
O botão "Finalizar compra" atualmente exibe uma mensagem de demonstração.  
Para ativar o checkout real, conecte um dos seguintes:

- **Shopify** — Substitua `doCheckout()` pelo Storefront API para criar uma URL de checkout nativa com Pix, cartão e boleto
- **Stripe** — Integre via Payment Links ou Checkout Session
- **Mercado Pago** — SDK JS disponível para checkout transparente
- **Yampi / Nuvemshop** — Se preferir uma plataforma nacional completa, migre o design para lá

### Newsletter
O formulário simula o envio. Para capturar emails de verdade:
- **Mailchimp** — adicione o endpoint do formulário embutido deles
- **Klaviyo** — use o JS SDK deles
- **ConvertKit / Brevo** — ambos têm APIs simples de subscribe

### Formulário de Contato
Atualmente mostra apenas um toast. Para receber as mensagens:
- **Formspree** — troque `onsubmit` pelo endpoint `https://formspree.io/f/SEU_ID`
- **Netlify Forms** — adicione `data-netlify="true"` no `<form>` (funciona automaticamente no Netlify)
- **EmailJS** — envia direto para seu email via JS, sem backend

### SEO e Analytics
Para rastrear visitas e aparecer no Google:
- Adicione o snippet do **Google Analytics 4** antes do `</head>`
- Adicione o **Google Search Console** e submeta o sitemap
- Configure **Open Graph** com imagens reais da campanha (o campo `og:image` está pronto para receber uma URL)

---

## Estrutura do arquivo

```
ajala.html
├── <head>          Google Fonts, meta tags, CSS completo (~700 linhas)
├── Header          Logo, navegação desktop, menu hamburguer, botão sacola
├── Mobile Menu     Overlay lateral com animação slide
├── Cart Drawer     Sacola lateral com linhas, quantidade, subtotal
├── Toast           Notificações animadas
├── #pg-home        Hero, Novidades, Banner, Categorias, Mais Desejados, Newsletter, Footer
├── #pg-shop        Busca, filtros, ordenação, grid de produtos
├── #pg-product     Galeria, seletor de tamanho/cor, adicionar à sacola
├── #pg-about       Hero com imagem, história, princípios, CTA
├── #pg-contact     Formulário de contato
├── #pg-privacy     Política de privacidade (LGPD)
├── #pg-404         Página não encontrada
└── <script>        Dados dos produtos, carrinho, navegação SPA, animações
```

---

## Personalização rápida

**Trocar cores:** edite as variáveis CSS no `:root` no início do `<style>`.

**Adicionar produto:** no `<script>`, adicione um objeto ao array `PRODS` seguindo o padrão dos existentes.

**Trocar imagens:** substitua as URLs no objeto `I` (CDN) pelas suas URLs de imagem.

**Alterar copy:** busque o texto no HTML e edite diretamente. Tudo está em pt-BR.

**Domínio customizado:** qualquer provedor (Vercel, Netlify, Cloudflare Pages) permite adicionar domínio próprio nas configurações do projeto.

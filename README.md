# Landing page — Doc das Milhas (grupo VIP no WhatsApp)

Site estático: HTML, CSS e JavaScript dentro de cada arquivo. **Não tem npm, build nem servidor.**

| Arquivo | O que é |
|---|---|
| `index.html` | a landing page |
| `politica-de-privacidade.html` | política de privacidade |
| `termos-de-uso.html` | termos de uso |
| `images/` | logo e ícone (gerados a partir da pasta `Identidade Visual`) |
| `robots.txt` / `sitemap.xml` | instruções para o Google |
| `CNAME` | domínio `docdasmilhas.com.br` para o GitHub Pages |

## 1. Ver o site

Dê dois cliques em `index.html`. Pronto.

## 2. Editar textos e preços

Abra o `.html` num editor de texto, procure o texto (Ctrl+F) e troque. Os preços aparecem em `index.html` (hero, planos) e em `termos-de-uso.html`.

## 3. Links de checkout, GTM

Tudo fica no bloco **CONFIGURAÇÃO**, no topo do `index.html`:

```js
const SITE = {
    checkoutAnual:  "https://pay.hotmart.com/...",   // link do plano anual
    checkoutMensal: "https://pay.hotmart.com/...",   // link do plano mensal
    gtmId: "GTM-XXXXXXX"                             // vazio = GTM desligado
};
```

Enquanto o checkout não estiver preenchido, os botões dos planos mostram um aviso em vez de quebrar.

## 4. Publicar (GitHub Pages)

Faça commit/push desta pasta, ou edite o arquivo direto no site do GitHub. A publicação leva 1–2 minutos.
Em *Settings → Pages*, aponte para a pasta/branch do site e ative **Enforce HTTPS**. No DNS do domínio, crie o registro indicado pelo GitHub.

## 5. Testar as UTMs

Abra `index.html?utm_source=teste&utm_campaign=beta&gclid=123`, passe o mouse (ou toque e segure) nos botões **Assinar o plano…** e confira se o link da Hotmart terminou com os mesmos parâmetros. Parâmetros repassados: `utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `utm_term`, `sck`, `gclid`, `gbraid`, `wbraid`, `fbclid`.

## 6. Analytics

- GA4, Google Ads e Meta Pixel são configurados **no painel do GTM**, não no código.
- O site envia só: `page_view` (GTM) e `cta_checkout_click` (clique em "Assinar o plano…", com `plano` e `cta`).
- `purchase` e `begin_checkout` vêm da **Hotmart** (configure Meta Pixel + API de Conversões e GA4 lá).
- O banner de cookies controla o Google Consent Mode (padrão: tudo negado).

## 7. O que a Hotmart faz (não está no site)

Checkout, Pix/Pix Automático, cartão, página de obrigado, **e-mail de compra aprovada com o link da Comunidade e o bônus do anual (Hotmart Send)**, renovação, cancelamento e reembolso.

> O link do grupo do WhatsApp **não fica no site**. Se vazar: revogue no WhatsApp, gere outro e atualize o e-mail do Hotmart Send.

## 8. O que é operação manual

Aprovar entradas na Comunidade, conferir a compra na Hotmart, registrar na **planilha de acessos (externa ao site)** e remover cancelados. Ver `operacao-diaria-doc-das-milhas-v3.md`.

## 9. Antes de lançar

1. Procure `PLACEHOLDER_BETA` em todos os arquivos — **não pode sobrar nenhum**.
2. Troque `<meta name="robots" content="noindex">` por `content="index, follow"` nos 3 arquivos `.html`.
3. Libere o `robots.txt` (instruções dentro dele).
4. Revise juridicamente as páginas legais e remova o aviso `REVISAR_JURIDICAMENTE_ANTES_DO_LANCAMENTO`.
5. Ative os depoimentos (bloco comentado no `index.html`) somente com depoimentos reais e autorizados.
6. Faça uma compra teste no cartão e outra no Pix, do anúncio até a entrada no grupo.

# Desafio Alongamento 21D — landing page

Site estático, sem build. Deploy na Vercel: é só importar o repositório, não há
nada para configurar.

```
index.html      página inteira (HTML + CSS + JS, 53 KB)
assets/         fotos antes/depois e retrato do professor
fonts/          as 3 famílias, subset latino, servidas do próprio domínio
favicon.svg     marca do goniômetro
vercel.json     cache de 1 ano em assets/fonts + headers de segurança
```

Para rodar local: `python3 -m http.server 8000` na raiz e abra
`http://localhost:8000`. Abrir o `index.html` direto por `file://` também
funciona.

Para trocar o retrato do professor, substitua `assets/daniel.jpg`. O
enquadramento usa `object-position:50% 18%` (puxa para o topo, priorizando o
rosto) — ajuste esse valor no `.portrait__img` se a nova foto pedir outro corte.

## O que falta preencher

Todo campo pendente está marcado no HTML com `<span class="edit">…</span>`
(aparece na página como um selo âmbar tracejado). São 12 marcas, em 5 lugares:

| Onde | O que preencher |
|---|---|
| Hero + CTA final | prazo da garantia em dias |
| Seção do professor | nº de alunos já guiados |
| Bloco de oferta | valor cheio, valor parcelado, valor à vista, período de acesso, confirmação do bônus "Guia de dor por região" |
| Bloco de garantia | nº de dias no selo e no texto |
| FAQ | canal de suporte (e-mail ou WhatsApp) |

Depois de preencher, apague a tag `<span class="edit">` em volta — o selo some.

## Trocas recomendadas

- **Avatares dos depoimentos**: hoje são monogramas (AS, CM, SP). Troque por
  fotos reais dos alunos assim que houver autorização de uso de imagem — as
  fotos de banco herdadas da página antiga foram removidas de propósito.
- **`og:image`**: falta definir. Com o domínio no ar, gere uma imagem 1200×630 e
  adicione `<meta property="og:image" content="https://SEU-DOMINIO/og.jpg">` —
  é o que aparece quando o link é colado no WhatsApp e no Instagram.
- **Termos de uso / Política de privacidade / Suporte** no rodapé estão com
  `href="#"`. Aponte para as páginas reais.

## Onde mexer no visual

Todas as cores e fontes ficam no bloco `:root` no topo do `<style>`:

```
--blue:   #1583EA   /* azul da marca, tirado das fotos do cliente */
--signal: #FFB020   /* âmbar, usado só nos botões de compra */
--ink:    #05080F   /* fundo */
```

Mudar `--blue` e `--signal` recolore a página inteira.

## Detalhes técnicos

- Link de checkout Hotmart em 6 CTAs: `pay.hotmart.com/G106599845O?off=5l9x9gnn`.
  Se o link da oferta mudar, busque e substitua as 6 ocorrências.
- Responsivo até 360px. Barra fixa de compra aparece no mobile após 60% da tela.
- Respeita `prefers-reduced-motion` (desliga as animações).
- Fontes vêm do Google Fonts (Bricolage Grotesque, Instrument Sans, IBM Plex
  Mono). Precisa de internet para renderizar com a tipografia correta.
- Rodapé tem disclaimer legal de saúde. Revise com quem cuida do jurídico do
  cliente antes de publicar.

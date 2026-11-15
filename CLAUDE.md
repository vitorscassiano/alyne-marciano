# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

Site one-page da Alyne Marciano (Psicóloga e Fonoaudióloga, especialista em Neuropsicologia). HTML, CSS e JS puros: sem build, sem dependências, sem testes. Todo o conteúdo é em pt-BR.

## Rodar e conferir

- Abra `index.html` no navegador. Não há servidor nem build.
- Para conferir sem abrir o navegador, use o Chrome headless:
  ```bash
  "/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars \
    --window-size=1280,900 --virtual-time-budget=3000 --screenshot=out.png "file://$PWD/index.html"
  ```
  - O hero ocupa a altura da janela e os elementos `.reveal` só aparecem ao rolar. Para um print da página inteira, use uma cópia temporária com `.hero{min-height:auto}` e `.reveal{opacity:1;transform:none}`.
  - O headless não abre janelas com menos de 500px de largura, então um print "de celular" sai cortado. Meça `document.documentElement.scrollWidth` antes de concluir que algo está vazando.

## Arquitetura

- `index.html` tem todo o texto. Cada seção é uma `<section id="...">`. Os comentários `✏️ EDITE` marcam o que a dona do site pode trocar, então mantenha-os.
- `assets/js/script.js` é uma IIFE sem dependências. O número do WhatsApp (`WHATSAPP`, por enquanto de exemplo) e a mensagem padrão ficam no topo. Ele cuida de:
  - preencher o link de todo elemento `[data-wa]`, então botões de agendamento usam `data-wa href="#"`;
  - o menu mobile e a sombra do header;
  - a animação `.reveal` (IntersectionObserver; `data-delay="1|2"` escalona);
  - os cards de público (`[data-publico]` abre o painel `[data-panel]` correspondente);
  - os blocos `.mais` (veja abaixo);
  - o acordeão do FAQ (`<details class="faq-item">`);
  - o formulário, que não tem backend: monta a mensagem e abre o WhatsApp.
- **Blocos "Saiba mais" (`.mais`)**: conteúdo longo fica recolhido atrás de um `button[data-mais]`. A altura anima entre `grid-template-rows: 0fr` e `1fr`, a mesma técnica do FAQ. Sem JS, tudo fica visível. Links para um `id` dentro de um bloco recolhido abrem o bloco antes de rolar até ele. A regra do projeto é mostrar título e introdução e esconder o detalhe: o visitante clica no que quer ler.
- SEO: `<head>` com canonical, Open Graph e JSON-LD (`MedicalBusiness`). O domínio `https://alynemarciano.com.br/` aparece no `index.html`, no `robots.txt` e no `sitemap.xml`. Ao mudar endereço, contatos ou domínio, atualize os três e o JSON-LD.

## Design (base do site)

Siga sempre este visual: tons pastéis, acolhedor, muito espaço em branco, cantos arredondados.

- **Cores**: use só as variáveis do `:root` em `assets/css/styles.css`, nunca hex solto.
  - Fundos: `--c-bg` (creme) e `--c-bg-soft`.
  - Destaque: `--c-sage-deep` (verde) em botões, eyebrows e marcadores.
  - Apoio: sálvia, lilás e rosé, cada um com uma versão `-soft` para fundos.
  - Texto: `--c-ink` e `--c-ink-soft`. Bordas: `--c-line`.
- **Fundo das seções**: alterne `.section-alt`, `.section-white`, `.section-blush` e `.section-lilac` para separar as seções sem usar linhas.
- **Ícones e etiquetas**: use `.tint-sage`, `.tint-lilac` ou `.tint-blush`. Os ícones são SVG inline de traço (`stroke="currentColor"`, `stroke-width` 1.8).
- **Fontes**: Lora (`--font-title`) nos títulos, com itálico em verde para destaque (`h1 em`). Nunito Sans (`--font-body`) no texto.
- **Formas**: `--radius` (22px) em cards, `--radius-sm` em itens menores, `--radius-pill` em botões e chips. Sombras: `--shadow` e `--shadow-soft`, ambas leves.
- **Componentes prontos** (reaproveite antes de criar outro):
  - cabeçalho de seção: `.section-head` com `.eyebrow`, `.section-title` e `.section-lead`;
  - botões: `.btn` com `.btn-primary` ou `.btn-ghost`;
  - `.card`, `.check-list` (marcador em bolinha verde), `.chip` e `.nota`.
- **Responsivo**: mobile-first, com breakpoints em 600px, 900px e 1180px (menu completo a partir de 1180px). Respeite `prefers-reduced-motion`.

## Conteúdo

- Os registros CRP 05/38142 e CRFa 1-15495 são obrigatórios. Eles aparecem no hero, no Sobre e no rodapé, então não remova todos.
- Use "Envelhecimento", não "Gerontologia". A Alyne ainda pode trocar o termo.
- Os contatos oficiais estão na seção Contato e no rodapé: e-mail, Instagram, TikTok e endereço. Mantenha os dois lugares iguais.
- As fotos ficam em `assets/img/`. Toda `<img>` leva `alt` descritivo, `width`/`height` e `loading="lazy"`.

## Git

- O repositório é público. `docs/` guarda os rascunhos da Alyne e não deve ser commitado.
- Antes de enviar commits para a branch de um PR, confira com `gh pr view` se ele ainda está aberto. Commits enviados depois do merge ficam fora da `main`.

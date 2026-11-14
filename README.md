# Site — Alyne Marciano · Neuropsicologia

Template profissional de site vertical (one-page) com cores pastéis,
100% responsivo, feito em HTML + CSS + JavaScript puros — sem build,
sem dependências. Basta abrir o `index.html` no navegador.

## Estrutura

```
.
├── index.html            # todo o conteúdo e textos do site
├── robots.txt            # SEO — regras para buscadores
├── sitemap.xml           # SEO — mapa do site para o Google
├── assets/
│   ├── css/styles.css    # cores, fontes e estilos (paleta no topo)
│   ├── js/script.js      # menu, animações, "Saiba mais", formulário → WhatsApp
│   └── img/              # fotos do site
└── docs/                 # materiais de referência (textos enviados pela Alyne)
```

`index.html`, `robots.txt` e `sitemap.xml` precisam ficar na raiz para o
site e os buscadores os encontrarem.

## Como editar

### Textos (tudo no `index.html`)

Procure pelos comentários `✏️ EDITE`. Estrutura das seções:

- **Início** — apresentação, atendimentos em destaque, registros (CRP / CRFa) e botão "Agendar horário"
- **Conheça os atendimentos** — cards por público (Infância e Adolescência /
  Adulto e Idoso); ao clicar, exibem os serviços de cada público
- **O que é Avaliação Neuropsicológica**
- **Infância e Adolescência** — 6 grupos de sinais (recolhidos no botão "Ver sinais por área")
- **Adulto e Envelhecimento** — introdução; sinais de alerta e impacto no dia a dia ficam recolhidos
- **Programa REAB** — como funciona, Fonoaudiologia neurológica,
  orientação a familiares e cuidadores (recolhidos no botão "Como funciona")
- **Psicoterapia** — infantil (presencial) e adultos (presencial e on-line)
- **Sobre Alyne**
- **FAQ** e **Contato** (o formulário inclui o atendimento de interesse)

### Blocos "Saiba mais"

Conteúdos longos ficam dentro de `<div class="mais">`: o botão
`.btn-mais` abre e fecha o trecho `.mais-conteudo`. Para mostrar algo
sempre aberto, basta movê-lo para fora desse bloco.

### Número do WhatsApp (`assets/js/script.js`, primeira linha)

```js
const WHATSAPP = "5521999999999" // 55 + DDD + número
```

Todos os botões ("Agendar conversa", botão flutuante e o formulário)
usam esse número automaticamente.

### Cores (`assets/css/styles.css`, bloco `:root` no topo)

Troque os valores das variáveis `--c-*` para mudar a paleta do site
inteiro de uma vez (fundo, verde sálvia, lilás, rosé…).

### Fotos

As áreas de foto são círculos decorativos com as iniciais "AM" e o
texto "sua foto aqui". Para trocar, substitua o elemento
`.hero-blob` (seção Início) e `.sobre-photo` (seção Sobre) por:

```html
<img src="assets/img/sua-foto.jpg" alt="Alyne Marciano" />
```

Os cards de público usam `assets/img/espaco-infantil.jpeg` e
`assets/img/espaco-adulto.jpeg`. Para trocar, substitua os arquivos
mantendo o mesmo nome (proporção ideal 4:3 ou 16:9).

### Registros profissionais

CRP 05/38142 e CRFa 1-15495 aparecem no Início, na seção Sobre e no
rodapé — a exibição é obrigatória.

## Publicar

O site é estático: pode ser hospedado de graça em qualquer um destes:

- **GitHub Pages** — suba os arquivos num repositório e ative Pages
- **Netlify** — arraste a pasta em [app.netlify.com/drop](https://app.netlify.com/drop)
- **Vercel** — `npx vercel` na pasta do projeto
- **Hostinger / GoDaddy** — envie os arquivos por FTP/cPanel

## Observações

- O formulário de contato não tem backend: ele monta a mensagem e
  abre o WhatsApp — perfeito para começar sem custo.
- Nota de segurança (CVV 188) no rodapé: recomendável manter.

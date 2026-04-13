# CLAUDE.md

## Projeto
BlindRank Site — Landing page do BlindRank (organizador de degustacoes de vinho com ranking coletivo). Site institucional/marketing que apresenta o produto e direciona para o app (`blindrank.wine`).

## Fase Atual
Fase 0: Prototipo estatico. HTML puro (857 linhas), sem framework, sem build, sem deploy.

## Relacao com o App Principal
O app de producao vive em `../blindrank/` (Next.js 14 + Supabase + Vercel). Este repositorio e exclusivamente o site institucional — nao compartilha codigo, mas compartilha design system, fontes e assets visuais.

## Como trabalhar
- Ler `CLAUDE.md`, `PLANNING.md` e `TASKS.md` no inicio de cada sessao.
- Declarar a task por ID antes de executar. Uma task por vez.
- Mudancas de UX/fluxo: plano curto antes de editar.
- Ao terminar: validar visualmente no browser, commit + push.

---

## Stack

- **HTML5 estatico** — arquivo unico `blindrank-landing-prototipo.html`
- **CSS3 embutido** — tokens do design system canonico do BlindRank
- **Fontes via CDN**: Eudoxus Sans (Fontshare), DM Sans + Playfair Display (Google Fonts)
- **Sem JavaScript** — animacoes via CSS (`animation-timeline: view()`, scroll-driven)
- **Sem build process** — abrir o HTML direto no browser

---

## Design System (compartilhado com o app)

### Cores
| Token | Valor | Uso |
|-------|-------|-----|
| `--t-accent` | `#8B1A00` | CTA bordo — exclusivo para botoes primarios |
| `--t-accent-hover` | `#6B1200` | Hover do CTA |
| `--t-text-1` | `#0a0a0a` | Texto principal |
| `--t-text-2` | `#3a3a3a` | Texto secundario |
| `--t-text-3` | `#767676` | Texto terciario (WCAG AA ajustado) |
| `--t-text-4` | `#bbbbbb` | Texto discreto |
| `--t-text-5` | `#e8e4de` | Texto sobre fundo escuro |
| `--tier-1` | `#C04000` | Destaque terracota |
| `--tier-2` | `#C47820` | Intermediario ambar |
| `--tier-3` | `#F0D080` | Base dourado |
| `--t-stroke` | `#0a0a0a` | Contornos |
| `--t-rule` | `rgba(10,10,10,0.08)` | Filetes e separadores |

### Tipografia
- **Eudoxus Sans** (`--font-display`): titulos, headlines, eyebrows. Pesos 400/500/600. Via Fontshare CDN.
- **DM Sans** (`--font-body`): corpo, paragrafos, labels. Pesos 400/500/600. Via Google Fonts.
- **Playfair Display**: nao usada diretamente no HTML atual, mas carregada no `<head>` (remover se nao necessario).

### Layout
- `--max-w: 1240px` — largura maxima do conteudo
- `--gutter: clamp(20px, 4vw, 56px)` — margem lateral responsiva

---

## Estrutura do Site

### Secoes (ordem no HTML)
1. **Header** — sticky, glassmorphism (backdrop-blur), logo SVG + link "Tenho um PIN"
2. **Hero** — headline "O ranking que faltava na sua mesa" + CTA bordo + device mockup (screenshot do app)
3. **Como Funciona** — 3 passos (criar, entrar pelo PIN, ranking)
4. **Momentos** — 3 artigos com screenshots (avaliando, completo, aguardando resultado)
5. **Para Quem E** — texto corrido (confrarias, sommeliers, importadores)
6. **Metodo** — colofao tecnico (agregacao, Borda Count, desempate, acervo). Fundo escuro `#0a0a0a`
7. **CTA Final** — "Pronto pra primeira?" + botao
8. **Footer** — marca, links (Termos, Privacidade, Contato), meta

### Links internos (apontam para o app)
- `/auth` — criar conta / login
- `/pin` — entrar como degustador
- `/termos` — termos de uso (nao existe ainda)
- `/privacidade` — politica de privacidade (nao existe ainda)
- `mailto:contato@blindrank.wine` — email de contato

---

## Assets

| Arquivo | Descricao |
|---------|-----------|
| `blindrank-logo-notag.svg` | Logo SVG com blur + stroke |
| `blindrank-logo-notag-780.png` | Logo PNG 780px |
| `blindrank-logo-notag-1560.png` | Logo PNG 1560px |
| `blindrank-logo-notag-3120.png` | Logo PNG 3120px |
| `blindrank-icon-bordo-512.png` | Icone bordo 512px |
| `blindrank-icon-bordo-1024.png` | Icone bordo 1024px |
| `blindrank-icon-inverted-512.png` | Icone invertido 512px |
| `blindrank-icon-inverted-1024.png` | Icone invertido 1024px |
| `blindrank-icon-primary-512.png` | Icone primario 512px |
| `blindrank-icon-primary-1024.png` | Icone primario 1024px |
| `blindrank-step-tasting-inicio.png` | Screenshot: tela de avaliacao (inicio) |
| `blindrank-step-tasting-progresso.png` | Screenshot: tela de avaliacao (progresso) |
| `blindrank-step-tasting-completo.png` | Screenshot: tela de avaliacao (completo) |
| `blindrank-aguardando-resultado.png` | Screenshot: tela de espera pos-submit |

---

## Animacoes

- **Scroll-driven** (`animation-timeline: view()`): elementos com classe `.reveal` animam entrada (opacity + translateY) ao entrar no viewport. Requer browser com suporte (Chrome 115+, Safari 18+). Firefox sem suporte nativo.
- **`prefers-reduced-motion`**: animacoes e scroll suave desabilitados.
- **Header glassmorphism**: `backdrop-filter: saturate(140%) blur(8px)`.

---

## Gotchas

### Fontes
- **Eudoxus Sans no site usa Fontshare CDN**, mas o app principal usa **font local** (`app/fonts/EudoxusSans-Variable.woff2`). Se migrar para framework compartilhado, unificar para font local.
- **Playfair Display** esta carregada no `<head>` mas nao e usada em nenhum elemento. Candidata a remocao.

### Compatibilidade
- **`animation-timeline: view()`** nao funciona no Firefox. Fallback: elementos aparecem estaticos (sem animacao). Aceitavel para MVP.
- **Glassmorphism** (`-webkit-backdrop-filter`) precisa de prefixo para Safari.

### Links
- Links `/auth`, `/pin`, `/termos`, `/privacidade` sao **relativos** — so funcionam se o site estiver no mesmo dominio do app. Se deployar em dominio separado, precisam virar URLs absolutas (`https://blindrank.wine/auth`).
- `/termos` e `/privacidade` **nao existem** no app atual — paginas a criar.

### SEO e Meta
- Faltam: Open Graph tags, Twitter Card, favicon, sitemap, robots.txt.
- `<title>` e `<meta description>` ja existem e estao bons.

### Responsividade
- Breakpoint unico: `max-width: 880px`.
- Hero e Momentos viram single-column no mobile.
- Footer centralizado no mobile.

---

## Vocabulario (herdado do app)
- **Vinho** = numero fisico na mesa (#1, #2). Nunca "amostra" na UI.
- **Rotulo** = identidade real (nome, produtor, safra).
- **Degustacao** (nunca "sessao"), **degustador**, **avaliacao** (nunca "voto").
- **Ranking** = resultado coletivo.

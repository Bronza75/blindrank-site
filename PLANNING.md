# PLANNING.md

## Objetivo
Transformar o prototipo estatico da landing page do BlindRank em site de producao, deployado em `blindrank.wine`, servindo como porta de entrada para o app.

## Fase Atual
**Fase 1: Deploy do prototipo.** Site no ar em `blindrank-site.vercel.app`. GitHub `Bronza75/blindrank-site` com auto-deploy. Dominio custom pendente.

---

## Roadmap

### Fase 1 — Deploy do prototipo (prioridade)
Colocar o que ja existe no ar. Sem refactor, sem framework.

- Inicializar git
- Deploy estatico (Vercel ou Netlify — HTML direto)
- Configurar dominio `blindrank.wine`
- Adicionar favicon, OG tags, Twitter Card
- Criar `robots.txt` e `sitemap.xml`
- Converter links relativos para URLs absolutas do app

### Fase 2 — Producao minima
Polimentos necessarios para um site publico profissional.

- Criar paginas `/termos` e `/privacidade`
- Otimizar imagens (WebP, srcset, lazy loading)
- Adicionar analytics (PostHog ou Vercel Analytics)
- Adicionar CTA secundario (ex: video demo, link para demo ao vivo)
- Testar acessibilidade (WCAG AA) e performance (Lighthouse)
- Remover Playfair Display se nao utilizada

### Fase 3 — Migracao para framework (quando justificado)
So migrar se houver necessidade real (i18n, blog, componentes dinamicos).

- Avaliar Next.js (SSG) vs Astro vs manter HTML
- Se migrar: compartilhar font local Eudoxus Sans com o app
- i18n da landing (pt-BR + en, no minimo)
- Blog ou changelog (opcional)
- Pricing page (se modelo de negocio definido)

---

## Decisoes Pendentes

| Decisao | Contexto | Status |
|---------|----------|--------|
| Dominio: `blindrank.wine` root ou subdominio? | Site e app no mesmo dominio simplifica links, mas pode complicar routing no Vercel | Pendente |
| Framework de migracao | Next.js (consistencia com app) vs Astro (mais leve para site estatico) vs manter HTML | Pendente — so decidir na Fase 3 |
| Paginas legais | `/termos` e `/privacidade` precisam de conteudo juridico | Pendente |
| Analytics | PostHog (ja usado no app) vs Vercel Analytics (mais simples) | Pendente |

---

## Concluido

**2026-04-13 — Documentacao + deploy**
Criados `CLAUDE.md`, `PLANNING.md` e `TASKS.md`. PostHog analytics integrado (snippet inline). Git inicializado, repo `Bronza75/blindrank-site` criado, deploy Vercel producao em `blindrank-site.vercel.app` com auto-deploy via GitHub.

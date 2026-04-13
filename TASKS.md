# TASKS.md

## Contexto
Fase ativa: Fase 1 — Deploy do prototipo. Site no ar em `blindrank-site.vercel.app`, GitHub conectado (auto-deploy).
Regra: trabalhar em uma task por vez e sempre citar o ID da task.

## Pendente

### Bloco A — Deploy do prototipo
- [x] SITE-A1 — Inicializar repositorio git + primeiro commit
- [x] SITE-A2 — Deploy estatico no Vercel (HTML direto, sem framework)
- [ ] SITE-A3 — Configurar dominio `blindrank.wine` no Vercel
- [ ] SITE-A4 — Adicionar favicon (usar `blindrank-icon-bordo-512.png` como base)
- [ ] SITE-A5 — Adicionar Open Graph tags + Twitter Card (titulo, descricao, imagem)
- [ ] SITE-A6 — Criar `robots.txt` + `sitemap.xml`
- [ ] SITE-A7 — Converter links relativos (`/auth`, `/pin`) para URLs absolutas do app

### Bloco B — Producao minima
- [ ] SITE-B1 — Criar pagina `/termos` (termos de uso)
- [ ] SITE-B2 — Criar pagina `/privacidade` (politica de privacidade)
- [ ] SITE-B3 — Otimizar imagens: converter PNGs para WebP, adicionar `srcset` e `loading="lazy"`
- [x] SITE-B4 — Adicionar analytics PostHog (wizard `@posthog/wizard`, snippet inline no HTML, public token `phc_yEh...`)
- [ ] SITE-B5 — Audit acessibilidade (WCAG AA) + performance (Lighthouse ≥90)
- [ ] SITE-B6 — Remover Playfair Display do `<head>` se confirmado que nao e usada

## Backlog

### Conteudo expandido
- [ ] SITE-C1 — Adicionar video demo ou GIF animado do fluxo de uso
- [ ] SITE-C2 — Secao FAQ (perguntas frequentes)
- [ ] SITE-C3 — Secao social proof (depoimentos ou numeros de uso)

### Migracao para framework (Fase 3 — so quando justificado)
- [ ] SITE-D1 — Avaliar Next.js SSG vs Astro vs manter HTML
- [ ] SITE-D2 — Migrar HTML para framework escolhido
- [ ] SITE-D3 — i18n da landing (pt-BR + en)
- [ ] SITE-D4 — Blog ou changelog (opcional)

## Concluido

### 2026-04-13
- [x] SITE-DOC — Criar CLAUDE.md, PLANNING.md e TASKS.md para o projeto
- [x] SITE-B4 — Adicionar analytics PostHog (wizard `@posthog/wizard`, snippet inline no HTML, public token)
- [x] SITE-A1 — Git init + primeiro commit (`07e0fcd`, 19 arquivos). Repo: `Bronza75/blindrank-site`
- [x] SITE-A2 — Deploy Vercel producao: `blindrank-site.vercel.app`. GitHub conectado (auto-deploy em push)

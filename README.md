# 📁 Ramos Portfólio — Documentação
 
Portfólio pessoal desenvolvido com **Astro**, focado em apresentar projetos, stack tecnológica e experiências como desenvolvedor backend. Inclui uma área de blog com suporte a Markdown e busca em tempo real.
 
🔗 **Deploy:** https://ramos902.github.io/portfolio/
 
---
 
## Estrutura de Pastas
 
```
RamosPortfolio/
├── public/
│   ├── favicon.ico
│   └── favicon.svg
└── src/
    ├── assets/
    │   ├── ramos.png                  → Foto de perfil (Hero)
    │   └── Projects/
    │       ├── ReceiteMeProject.png   → Preview do projeto ReceiteMe
    │       └── AryaInstallProject.png → Preview do projeto Arya
    ├── components/
    │   ├── HeaderPortfolio.astro      → Header fixo do portfólio (nav + tema)
    │   ├── HeaderBlog.astro           → Header do blog (busca + tema)
    │   ├── Hero.astro                 → Seção inicial com nome, stack e foto
    │   ├── AboutStack.astro           → Seção Sobre + cards de tecnologias
    │   ├── Projects.astro             → Cards de projetos com efeito 3D
    │   ├── BlogPost.astro             → Layout de post individual
    │   └── Loader.astro               → Tela de carregamento com barra de progresso
    ├── content/
    │   └── blog/
    │       ├── config.ts              → Schema da collection de posts
    │       └── *.md                   → Arquivos de posts em Markdown
    ├── layouts/
    │   └── Layout.astro               → Layout base (head, body, global.css)
    ├── pages/
    │   ├── index.astro                → Redireciona para /portfolio/
    │   └── blog/
    │       ├── index.astro            → Listagem de posts com busca
    │       └── [slug].astro           → Página individual de post
    └── styles/
        └── global.css                 → Reset, variáveis CSS e estilos base
```
 
---
 
## Paleta de Cores
 
### Light Theme (padrão)
 
| Variável         | Valor     | Uso                              |
|------------------|-----------|----------------------------------|
| `--bg-primary`   | `#f5f5f5` | Fundo principal                  |
| `--bg-secondary` | `#e5e7eb` | Fundo de cards e elementos       |
| `--accent`       | `#ff2a2a` | Cor de destaque, links ativos    |
| `--accent-glow`  | `#ff6b6b` | Glow do accent                   |
| `--text-primary` | `#0a0a0a` | Texto principal                  |
| `--text-muted`   | `#4b5563` | Texto secundário                 |
| `--border`       | `#d1d5db` | Bordas e divisores               |
 
### Dark Theme (manual ou auto)
 
| Variável         | Valor     | Uso                              |
|------------------|-----------|----------------------------------|
| `--bg-primary`   | `#000000` | Fundo principal                  |
| `--bg-secondary` | `#101010` | Fundo de cards e elementos       |
| `--accent`       | `#ff1f1f` | Cor de destaque, links ativos    |
| `--accent-glow`  | `#ff3b3b` | Glow do accent                   |
| `--text-primary` | `#ffffff` | Texto principal                  |
| `--text-muted`   | `#6b7280` | Texto secundário                 |
| `--border`       | `#505050` | Bordas e divisores               |
 
> O tema escuro é aplicado via `prefers-color-scheme` automaticamente ou manualmente pelo botão `◐` no header, persistido via `localStorage`.
 
---
 
## Tipografia
 
| Fonte       | Uso                                              | Como é carregada       |
|-------------|--------------------------------------------------|------------------------|
| **Georgia** | Headings (`h1`), títulos de cards e posts, logo  | Fonte do sistema       |
| **Inter**   | Corpo de texto geral (`body`)                    | Google Fonts (externo) |
| **monospace**| Labels, tags, nav links, código inline           | Fonte do sistema       |
 
### Tamanhos de fonte relevantes
 
| Elemento            | Tamanho                          |
|---------------------|----------------------------------|
| `h1` Hero           | `clamp(2.4rem, 5vw, 3.8rem)`     |
| `h1` Blog           | `clamp(2.2rem, 5vw, 3.2rem)`     |
| `h2` Sobre          | `clamp(1.8rem, 3vw, 2.6rem)`     |
| Nav links           | `0.78rem`                        |
| Section labels      | `0.72rem`                        |
| Tags / badges       | `0.68rem – 0.7rem`               |
| Descrições / muted  | `0.78rem – 0.95rem`              |
| Body padrão         | `1rem` (16px)                    |
 
---
 
## Rotas
 
| URL                        | Descrição                        |
|----------------------------|----------------------------------|
| `/portfolio/`              | Página principal do portfólio    |
| `/portfolio/blog/`         | Listagem de posts do blog        |
| `/portfolio/blog/[slug]`   | Post individual                  |
 
---
 
## Blog — Frontmatter dos posts
 
Cada arquivo `.md` em `src/content/blog/` deve seguir o schema:
 
```yaml
---
title: "Título do post"
description: "Descrição curta"
date: 2025-04-01
postId: 1
tags: ["tag1", "tag2"]
---
```
 
---
 
## Configuração do Projeto
 
**`astro.config.mjs`**
```js
export default defineConfig({
  site: 'https://ramos902.github.io',
  base: '/portfolio',
});
```
 
**Deploy:** GitHub Actions via `.github/workflows/astro.yml` usando `withastro/action@v3`, com `path: ./RamosPortfolio`.
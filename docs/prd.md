# Product Requirements Document (PRD)

## Minimalist Full-Stack Developer Portfolio

A state-of-the-art, ultra-minimalist, full-stack portfolio designed for modern software engineers. It facilitates seamless showcase of projects, publishing of blog posts, and dynamic dashboard-driven content management without code redeployment, using **Next.js, Tailwind CSS, Supabase, and Vercel**.

---

## 1. Objective & Vision
The objective is to build a premium, highly performant web presence that serves as a living portfolio, writing medium, and technical showcase. 
* **The Vision**: Establish a monochromatic, typography-centric digital presence that radiates technical excellence, clean code sensibilities, and professional maturity.
* **The Goal**: High-performance (100 Lighthouse score), ultra-fast page transitions, deep SEO optimization, and a seamless dashboard experience for modifying data on the fly.

---

## 2. Target Audience
1. **Engineering Managers & Recruiters**: Seeking structured, quickly scanable technical competencies, architecture diagrams, and repository connections.
2. **Technical Readers / Developers**: Seeking readable, clean code blocks and engineering insights in the blog section.
3. **General Public**: Interested in high-level descriptions of software solutions.

---

## 3. Core Features

### A. Hero & Identity
* **Headline**: An impactful, minimalist typographic statement with a custom dynamic intro (e.g., typing effect or fading micro-animations).
* **Bio**: A concise, highly polished 2-sentence description of engineering principles and current focus.
* **Social Connections**: Floating or docked minimalist interactive SVGs pointing to GitHub, LinkedIn, and email with immediate feedback copy-to-clipboard animations.

### B. Project Showcase
* **Featured Projects Grid**: A curated showcase of top tier works using sleek typography and line-art borders.
* **Filter/Search**: Real-time filtering by stack tags (e.g., "Next.js", "Go", "PostgreSQL") using smooth client-side filtering.
* **Project Details (Modal or Sub-page)**:
  - Deep-dive technical explanations of challenges and architecture.
  - Interactive "System Design Viewer" or clean component-tree breakdown.
  - Production URL and source code link with dynamic status indicators.

### C. Technical Blog
* **Readability First**: Optimized reading layout (max-width `prose` container, carefully tuned line-height, large typography).
* **MDX Support**: Full markdown capability with syntax highlighting for code blocks (using Prism or Shiki), table of contents, and interactive embedded React elements.
* **Search & Categorization**: Fast client-side keyword search and tag classification.
* **Analytics & Performance**: Incremental Static Regeneration (ISR) combined with stale-while-revalidate caching ensures zero-latency post loads.

### D. Centralized Admin Dashboard (Private Router)
* **Secure Auth**: Next.js Middleware protection linked with Supabase Auth.
* **Project Manager**: Create, Read, Update, Delete (CRUD) operations on projects, including drag-and-drop ordering and image/media upload directly to Supabase Storage.
* **Blog Editor**: Markdown-enabled web editor to write, preview, save as draft, or publish technical write-ups.
* **Analytics Overview**: Clean visualization of read times, portfolio views, and contact submissions.

### E. Theme Orchestration
* **System-Preferential Light/Dark Mode**: Seamless light and dark mode toggler that aligns with system preferences by default but allows persistable override. Zero flash of unstyled content (FOUC).

---

## 4. User Stories

### For the Owner (Admin)
* *As an administrator*, I want to log in securely through a private dashboard so I can manage my portfolio content on any device without committing new code.
* *As an author*, I want a clean markdown editor with side-by-side preview so I can format complex code blocks and tables easily.
* *As an owner*, I want to upload high-fidelity PNG/SVG mockups directly to Supabase Storage so that my project pages look visually flawless.

### For the Visitor
* *As a recruiter*, I want to immediately see which projects represent the developer's strongest full-stack work, filtering down to those with Next.js or Go backends.
* *As a developer*, I want to search through technical blog posts and read snippets with syntax-highlighted code.
* *As a reader*, I want a seamless dark/light mode toggle that changes colors without jarring jumps, allowing comfortable reading.

---

## 5. Prioritization Framework (ICE Matrix)
To optimize resources and assist AI/developer prioritization, tasks are scored using the **ICE Framework** (Impact × Confidence × Ease, scaled 1–10).

$$\text{ICE Score} = \frac{\text{Impact} \times \text{Confidence} \times \text{Ease}}{10}$$

| Phase | Epics & Tasks | Impact | Confidence | Ease | ICE Score | Priority |
| :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **Phase 1** | **Base Infrastructure** (Next.js Setup, Supabase Schemas, Vercel Deploy) | 10 | 10 | 9 | **90.0** | **P0** |
| **Phase 1** | **Database & Auth Integration** (Supabase Auth Client, CRUD API routes) | 9 | 9 | 8 | **64.8** | **P0** |
| **Phase 2** | **Minimalist Responsive UI** (Grid layouts, CSS Variable structure, Dark Mode) | 9 | 10 | 7 | **63.0** | **P1** |
| **Phase 2** | **Projects & Blog Display Engine** (Static Generation, Slug routes, MDX parser) | 8 | 9 | 7 | **50.4** | **P1** |
| **Phase 3** | **Admin Dashboard Panel** (Markdown WYSIWYG, CRUD panel UI) | 7 | 8 | 6 | **33.6** | **P2** |
| **Phase 4** | **Premium Polish** (Framer Motion page transitions, magnetic hovers, analytics) | 6 | 7 | 6 | **25.2** | **P3** |

---

## 6. Functional & Non-Functional Guidelines

### SEO & Performance Guidelines
* **Metadata API**: Leverage Next.js 15 metadata orchestration for robust OpenGraph, Twitter cards, and structured JSON-LD data.
* **Lighthouse Metrics**: Target 100 on Performance, Accessibility, Best Practices, and SEO.
* **Core Web Vitals**: LCP under 1.2s, CLS at 0, FID under 50ms.

### Deployment & CI/CD
* **Hosting**: Native deployment on Vercel.
* **Continuous Integration**: GitHub Actions configuration for linting, typing checks, and PR previews.
* **Database Mirroring**: Supabase database migration control tracked in git.

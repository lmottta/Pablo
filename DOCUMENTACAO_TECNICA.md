# Documentação Técnica do Portfólio de Pablo Luan

## Visão Geral do Projeto

Este é um portfólio profissional desenvolvido com HTML, Tailwind CSS (via CDN) e JavaScript, apresentando as habilidades, experiência e formação de Pablo Luan, Analista de Dados e Especialista Qlik com mais de 7 anos de experiência.

## Sistema de Design

### Paleta de Cores

Definida no `tailwind.config` (dentro do próprio `index.html`):

| Variável | Valor | Descrição |
|----------|-------|-----------|
| **Primária** | `#0a1a0f` | Verde escuro quase preto |
| **Secundária** | `#122b18` | Verde escuro |
| **Destaque (accent)** | `#52c41a` | Verde Qlik |
| **Verde Escuro (darkGreen)** | `#051208` | Verde quase preto |
| **Verde Médio (midGreen)** | `#2e6b37` | Verde médio |
| **Verde Claro (lightGreen)** | `#84cc16` | Lima brilhante |
| **Superfície (surface)** | `#0f1f14` | Cor de superfície escura |
| **Superfície Suave (surfaceSoft)** | `#162e1d` | Superfície levemente mais clara |
| **Neon** | `#73d13d` | Verde neon Qlik |
| **Highlight** | `#facc15` | Amarelo para contraste |

### Tipografia

- **Fonte**: Poppins (do Google Fonts)
- **Pesos**: 300, 400, 500, 600, 700
- **Cores de Texto**:
  - Primário: `text-slate-100` (off-white)
  - Secundário: `text-slate-300` (cinza claro)
  - Mudo: `text-slate-400` (cinza médio)

### Fundos

- **Corpo**: Gradiente complexo com múltiplos gradientes radiais e linear:
  ```css
  background-color: #0a1a0f;
  background-image: radial-gradient(circle at 20% 20%, rgba(132, 204, 22, 0.12), transparent 35%),
                    radial-gradient(circle at 85% 15%, rgba(82, 196, 26, 0.18), transparent 30%),
                    radial-gradient(circle at 75% 80%, rgba(115, 209, 61, 0.12), transparent 35%),
                    linear-gradient(145deg, #051208 0%, #0a1a0f 45%, #122b18 100%);
  background-attachment: fixed;
  ```

### Classes Reutilizáveis (em `<style>`)

- `.gradient-text`: gradiente de texto `linear-gradient(90deg, #73d13d, #84cc16, #52c41a)` com `background-clip: text`.
- `.surface-panel`: fundo `rgba(15, 31, 20, 0.8)`, `backdrop-filter: blur(20px)`, borda `rgba(115, 209, 61, 0.15)`, raio `1rem`.
- `.surface-panel-soft`: fundo `rgba(22, 46, 29, 0.6)`, mesma borda e desfoque.
- `.animate-float`: animação `float` 6s (deslocamento vertical de -15px).
- `.reveal` / `.reveal.visible`: transição de opacidade e `translateY(30px)` para 0.
- `.skill-bar`: barra com `background: linear-gradient(90deg, #73d13d, #52c41a)`.
- `.tab-btn` / `.tab-btn.active`: aba ativa com `background: rgba(115, 209, 61, 0.1)`, cor `#73d13d` e borda esquerda neon.
- `.form-input:focus`: borda `#73d13d` e `box-shadow: 0 0 0 3px rgba(115, 209, 61, 0.15)`.

## Estrutura e Layout

### Layout Global

- **Largura do Container**: `max-w-7xl mx-auto px-4 sm:px-6 lg:px-8`
- **Padding das Seções**: `py-20` (80px topo/baixo)
- **Seção Hero**: `min-h-screen flex items-center justify-center pt-28 pb-16`
- **Comportamento de Rolagem**: Suavizado globalmente (`html { scroll-behavior: smooth; }`)

### Pontos de Quebra Responsivos

- Mobile: padrão
- sm: 640px
- md: 768px
- lg: 1024px

## Detalhes dos Componentes

### Navbar

- Fixa no topo (`fixed top-0 inset-x-0 z-50`), com menu mobile togglável.
- Links: `text-slate-300 hover:text-neon transition-colors text-sm font-medium`.
- Menu mobile: `bg-darkGreen/95 backdrop-blur-xl border-t border-white/10`.

### Seção Hero (`#hero`)

- **Layout**: Flex coluna em mobile, flex linha em md+
- **Animações**: `.reveal` para entrada e `.animate-float` na imagem do perfil
- **Tipografia**:
  - Badge: `inline-flex px-4 py-2 rounded-full border border-neon/40 bg-neon/10 text-sm text-neon`
  - Nome: `text-4xl sm:text-5xl md:text-6xl font-semibold mb-4 tracking-tight gradient-text`
  - Descrição: `text-slate-300 text-lg mb-8 max-w-xl leading-relaxed`
- **Botões**:
  - Primário: `bg-gradient-to-r from-accent to-midGreen` com hover e elevação
  - Secundário: `border border-neon/50 text-neon hover:bg-neon/10`
  - Download CV: `border border-neutral-700 bg-neutral-800 text-slate-300 hover:text-neon`, link para `download-cv.html`
- **Imagem do perfil**: circular com `border-4 border-neon/40` e brilho `shadow-[0_0_60px_rgba(115,209,61,0.35)]`

### Seção Sobre (`#sobre`)

- **Layout**: Grid de duas colunas em md+ (texto | informações do perfil)
- **Cards**:
  - Esquerdo: `surface-panel p-8`
  - Direito: `surface-panel-soft p-8`
- **Tipografia**:
  - Título da Seção: `section-title gradient-text`
  - Subtítulos: `text-2xl font-semibold mb-4 text-slate-100`
  - Corpo: `text-slate-300 leading-relaxed`
  - Rótulos: `text-slate-400`
  - Valores: `text-slate-100 font-medium`

### Seção Experiência (`#experiencia`)

- **Layout**: Grid `md:grid-cols-[260px_1fr]` — abas à esquerda, conteúdo à direita
- **Fundo**: `bg-gradient-to-b from-darkGreen/50 to-primary/20`
- **Barra de Abas**:
  - Aba ativa: `.tab-btn.active` (`bg-neon/10 text-neon border-l-4 border-neon`)
  - Aba inativa: `text-slate-400 hover:text-slate-200 hover:bg-white/5 border-l-4 border-transparent`
- **Painéis de Conteúdo**:
  - Container: `surface-panel p-7`
  - Conteúdo gerado via JavaScript a partir do array de experiências
  - Itens com acento neon e seção de impacto destacada

### Seção Habilidades (`#habilidades`)

- **Layout**: `#skills-categories` grid `md:grid-cols-2`; `#tools-grid` grid responsiva 2/3/4/6 colunas
- **Cards de Categoria**:
  - Container: `surface-panel-soft p-6`
  - Título: `text-xl font-semibold mb-6 text-center gradient-text tracking-tight`
  - Barra de Progresso: container `w-full bg-slate-800 rounded-full h-2.5`, preenchimento `.skill-bar` com `linear-gradient(90deg, #73d13d, #52c41a)`
  - Animação das barras via `IntersectionObserver`
- **Ferramentas**: `surface-panel-soft p-4 text-center border border-white/10 hover:border-neon/40 rounded-xl hover:-translate-y-1`

### Seção Certificações (`#certificacoes`)

- **Layout**: `#certifications-grid` grid `md:grid-cols-2`; `#education-list` em lista vertical
- **Fundo**: `bg-gradient-to-b from-darkGreen/50 to-primary/20`
- **Cards de Certificação**: `surface-panel-soft p-6 flex items-start gap-4`
- **Cards de Formação**: `surface-panel p-6 border-l-4 border-neon/60`

### Seção Contato (`#contato`)

- **Layout**: Grid de duas colunas (informações de contato | formulário)
- **Cartão de Informações**: `surface-panel p-8`
  - Itens: ícone em `bg-neon/10 p-3 rounded-full text-neon`
  - Rótulos: `text-lg font-medium text-slate-100`
  - Valores: `text-slate-300 mt-1`
  - **E-mail**: link `mailto:pabloluan6798@gmail.com`
  - **WhatsApp**: link `https://wa.me/61996958368` com mensagem pré-preenchida "Olá Pablo, gostaria de entender mais sobre suas experiências"
  - **LinkedIn**: link para `/in/pablo-luan`
- **Cartão do Formulário**: `surface-panel-soft p-8`
  - Campos com classe `form-input` e foco neon
  - Feedback de sucesso/erro via `#form-feedback`
  - Botão de envio com gradiente e estado desativado

### Rodapé

- **Estilização**: fundo escuro com borda superior e ano dinâmico via JavaScript (`#year`)
- Links de navegação e informações de contato com acento neon no hover

## Detalhes de UI/UX

### Elementos Interativos

- **Botões**: gradientes e transições suaves (`transition-all duration-300`)
- **Links**: mudança de cor para neon no hover
- **Cards**: `backdrop-blur`, sombras e elevação leve no hover
- **Formulário**: foco neon, validação de erro (vermelho) e sucesso (verde)
- **Navegação**: aba ativa com borda neon e transições suaves

### Animações e Movimento

- **CSS**: `float`, `fadeInUp`, `.reveal`, animação de barras via `IntersectionObserver`
- **JavaScript**: geração dinâmica de tabs, skills, ferramentas, certificações e formação

### Acessibilidade

- **HTML Semântico**: uso de `header`, `nav`, `section`, `footer`
- **Texto Alternativo**: presente na imagem do perfil (`alt="Pablo Luan"`)
- **Associações de Rótulo**: rótulos de formulário vinculados aos inputs
- **Contraste de Cor**: fundo escuro com texto claro (verde neon sobre verde escuro)
- **Design Responsivo**: adapta-se a mobile, tablet e desktop
- **Atributo de Idioma**: `lang="pt-BR"` no elemento HTML

### Considerações de Performance

- **Tailwind via CDN**: sem etapa de build
- **Fontes**: Google Fonts com `display=swap`
- **Imagens**: fallback `onerror` para avatar gerado
- **Animação**: `IntersectionObserver` para ativar barras e revelações apenas quando visíveis

## Stack Técnico

### Frontend

- **Framework**: HTML5 estático + JavaScript (Vanilla)
- **Estilização**: Tailwind CSS 3.x (CDN)
- **Animações**: CSS Keyframes + IntersectionObserver
- **Fontes**: Google Fonts (Poppins)
- **Ícones**: SVG inline
- **Gerenciamento de Estado**: JavaScript (sem framework)
- **Tratamento de Formulário**: JavaScript com simulação de envio

### Ferramentas de Build e Desenvolvimento

- **Empacotador**: não se aplica (arquivo único)
- **PostCSS**: não se aplica
- **Verificação de Tipos**: não se aplica
- **Desenvolvimento**: abrir `index.html` diretamente no navegador

## Arquivos de Configuração

- `index.html`: página única com configuração Tailwind embutida, estilos e scripts
- `download-cv.html`: currículo em formato ATS para impressão/PDF
- `pablo.jpg`: foto de perfil (com fallback)

## SEO e Metadados

- **Título da Página**: "Pablo Luan · Analista de Dados & Especialista Qlik"
- **Descrição Meta**: presente no `<head>`
- **Theme Color**: `#051208`
- **Viewport**: tag de viewport móvel adequada
- **Estrutura Semântica**: hierarquia adequada de títulos (h1-h3)
- **Idioma**: português (pt-BR) especificado
- **Open Graph/Twitter Cards**: não explicitamente visível

## Responsividade Mobile

- **Pontos de Quebra**: quebras padrão do Tailwind (sm, md, lg)
- **Adaptações de Layout**:
  - Hero: Coluna → Linha
  - Sobre: Empilhado → Lado a lado
  - Habilidades: Coluna única → Duas colunas para categorias
  - Experiência: Abas verticais → Layout horizontal em telas maiores
  - Contato: Empilhado → Lado a lado
  - Rodapé: Três colunas em desktop, empilhado em mobile
- **Alvos de Toque**: adequadamente dimensionados botões e links
- **Tipografia**: tamanhos de fonte responsivos (prefixos sm:, md:)

## Qualidade do Código e Padrões

- **Arquitetura**: página única com dados gerados dinamicamente via JavaScript
- **Classes Reutilizáveis**: `section-title`, `gradient-text`, `surface-panel`, `surface-panel-soft`, `tab-btn`, `skill-bar`, `form-input`
- **Separação de Dados**: dados de experiência, skills, certificações e formação em arrays JavaScript no próprio arquivo
- **Tratamento de Erros**: validação básica de formulário e fallback de imagem
- **Acessibilidade**: atenção a aria-labels e estrutura adequada de títulos
- **Performance**: `IntersectionObserver`, CSS eficiente e fontes com `display=swap`

## Áreas para Melhoria

1. **Migração para build**: adotar um bundler para otimizar o CSS Tailwind
2. **Externalização de Conteúdo**: mover dados para JSON ou CMS
3. **Auditoria de Acessibilidade**: verificação formal de conformidade WCAG
4. **Monitoramento de Performance**: adicionar Lighthouse CI ou similar
5. **Testes**: adicionar testes de integração
6. **Internacionalização**: preparar para i18n se expandir suporte a idiomas
7. **Integração de Análise**: adicionar Google Analytics ou similar
8. **Formulário real**: substituir a simulação por um endpoint (Formspree, EmailJS, etc.)

## Resumo

Este site de portfólio demonstra uma implementação moderna e profissional com atenção a:

- **Design Visual**: tema escuro sofisticado com acentos neon verdes (identidade Qlik), gradientes e efeitos de glassmorphism
- **Experiência do Usuário**: animações suaves, navegação intuitiva, layouts responsivos
- **Implementação Técnica**: HTML estático, estilização eficiente com Tailwind (CDN) e JavaScript para conteúdo dinâmico
- **Acessibilidade**: consideração para contraste de cor, estados de foco e estrutura semântica
- **Apresentação Profissional**: vitrine abrangente de habilidades e experiência adequada para um analista de dados sênior

O design equilibra criatividade e profissionalismo, usando as cores de acento neon verde e gradientes para criar interesse visual mantendo a legibilidade e uma identidade de marca coesa ao longo do site. O currículo ATS (`download-cv.html`) mantém o mesmo padrão de cor do header do perfil para consistência de marca.

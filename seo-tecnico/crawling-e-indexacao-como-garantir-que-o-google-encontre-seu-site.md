# Crawling e Indexação: Como Garantir Que o Google Encontre Seu Site

Crawling e indexação são os dois processos fundamentais que determinam se o seu site existe para o Google. Crawling (rastreamento) é como o Google descobre suas páginas, enviando o Googlebot para percorrer links e coletar informações. Indexação é como o Google armazena e organiza essas páginas no seu índice, tornando-as elegíveis para aparecer nos resultados de busca. Se o Google não rastreia uma página, ela não é indexada. Se não é indexada, não rankeia. Não importa quão bom seja o conteúdo, quão forte seja a autoridade ou quão otimizado esteja o [on-page](../fundamentos-de-seo/seo-on-page-otimizacao-dentro-do-seu-site.md): uma página que o Google não encontra é uma página que não existe nos resultados de busca.

Esta página cobre em profundidade como o rastreamento funciona, o que é crawl budget e por que ele importa, como a indexação transforma páginas rastreadas em resultados de busca e como diagnosticar problemas que impedem seu conteúdo de ser encontrado.

---

## 🕷️ Rastreamento: Como o Google Encontra Suas Páginas

Rastreamento (crawling) é o processo pelo qual o [Google](../fundamentos-de-seo/como-funciona-o-google-rastreamento-indexacao-e-rankeamento.md) descobre páginas novas e atualizadas na web. O Googlebot, o crawler do Google, visita URLs, analisa o conteúdo e segue os links encontrados para descobrir mais páginas. Esse processo é contínuo: o Googlebot está constantemente revisitando páginas já conhecidas (para detectar atualizações) e descobrindo páginas novas (por meio de links ou sitemaps).

O rastreamento é o primeiro estágio do pipeline: sem ele, nada mais acontece. Entender como controlá-lo é essencial para garantir que o Google gaste seu tempo nas páginas que importam para o seu negócio.

### Googlebot e o Processo de Crawling

O Googlebot opera como um navegador automatizado. Ele faz requisições HTTP às páginas, recebe o HTML (e, quando necessário, executa JavaScript), analisa o conteúdo e extrai todos os links encontrados para adicioná-los à fila de rastreamento.

O processo segue uma lógica de priorização: o Google não rastreia todas as páginas com a mesma frequência. Páginas que mudam frequentemente (homepages, feeds de notícias) são revisitadas com mais frequência. Páginas estáticas que raramente mudam são revisitadas com menos frequência. Páginas com mais links internos e externos apontando para elas recebem prioridade de rastreamento.

É importante entender: o Googlebot rastreia a versão mobile do site por padrão (mobile-first indexing). Se a versão mobile do seu site tem menos conteúdo, menos links internos ou funcionalidade reduzida em relação à versão desktop, é a versão limitada que o Google está processando, com consequências diretas no rankeamento.

### Robots.txt: Quando Bloquear e Quando Liberar

O arquivo robots.txt é o mecanismo que controla quais áreas do site o Googlebot pode ou não rastrear. Localizado na raiz do domínio (`seusite.com.br/robots.txt`), ele contém diretivas que permitem ou bloqueiam o acesso a diretórios e URLs específicas.

**Quando bloquear:** páginas de administração, áreas de login, páginas de busca interna (que geram URLs infinitas), versões de impressão, páginas de staging/teste, e recursos que não devem ser indexados (PDFs internos, arquivos de mídia sem valor para busca).

**Quando NÃO bloquear:** CSS e JavaScript necessários para renderizar a página (o Googlebot precisa deles para entender o conteúdo), imagens relevantes para o conteúdo, e qualquer página que você deseja que apareça nos resultados de busca.

Um erro crítico e surpreendentemente comum: bloquear no robots.txt páginas que deveriam ser indexadas. Isso acontece frequentemente em migrações de site, quando o robots.txt do ambiente de staging (que bloqueia tudo) é copiado para produção. O resultado: o site inteiro desaparece do Google. A TRIWI já identificou e corrigiu esse problema em auditorias de múltiplos clientes; é um dos primeiros itens verificados em qualquer diagnóstico técnico.

Uma nuance importante: robots.txt impede o rastreamento, não a indexação. Se uma página é bloqueada no robots.txt mas tem links externos apontando para ela, o Google pode indexar a URL (sem conteúdo) com base nas informações dos links. Para impedir a indexação, use meta robots noindex, que é lido apenas se a página for rastreada. As duas diretivas têm funções diferentes e complementares.

### Sitemap XML: O Mapa do Seu Site

O sitemap XML é um arquivo que lista todas as URLs do site que você deseja que o Google conheça e rastreie. Funciona como um mapa entregue diretamente ao Googlebot: "estas são as páginas importantes do meu site, nesta prioridade, com estas datas de atualização."

O sitemap não garante indexação; é uma sugestão, não uma ordem. Mas para sites grandes ou com [arquitetura](arquitetura-de-site-para-seo.md) complexa, o sitemap é frequentemente a forma mais eficiente de garantir que o Google descubra todas as páginas importantes, especialmente aquelas que têm poucos links internos apontando para elas.

**Boas práticas de sitemap XML:**

Incluir apenas URLs que devem ser indexadas, páginas com noindex, redirecionamentos ou erros 404 não devem estar no sitemap. Manter atualizado, o sitemap deve refletir o estado atual do site, não uma versão de meses atrás. Segmentar por tipo, sites grandes se beneficiam de sitemaps separados por seção (blog, produtos, categorias) referenciados por um sitemap index. Incluir a tag `<lastmod>` com datas reais de modificação, isso ajuda o Google a priorizar o rastreamento de conteúdo atualizado. Submeter no Google Search Console, embora o Google descubra sitemaps automaticamente (via robots.txt), a submissão manual no Search Console acelera o processo e fornece relatórios de status.

---

## 📊 Crawl Budget: O Recurso Que Grandes Sites Não Podem Ignorar

Crawl budget é a combinação de dois fatores: o crawl rate limit (quantas requisições simultâneas o Googlebot pode fazer sem sobrecarregar o servidor) e o crawl demand (o interesse do Google em rastrear as URLs do site). Juntos, determinam quantas páginas do seu site o Google rastreia em um período de tempo.

### O Que é e Por Que Importa

Para sites pequenos (até 1.000 páginas), crawl budget raramente é um problema. O Google tem capacidade de sobra para rastrear tudo. Mas para sites enterprise, e-commerces com dezenas de milhares de produtos, portais de conteúdo com milhares de artigos, plataformas com URLs geradas dinamicamente, o crawl budget se torna um recurso finito e crítico.

Quando o crawl budget é desperdiçado em páginas de baixo valor (parâmetros de URL, filtros de busca interna, variações sem conteúdo único), sobra menos budget para as páginas que realmente importam. O resultado: conteúdo novo demora para ser descoberto, atualizações de páginas existentes não são detectadas, e páginas estratégicas são rastreadas com menos frequência, comprometendo a frescura da indexação e, por consequência, o rankeamento.

### Sinais Que Indicam Problemas de Crawl Budget

**Páginas novas demorando semanas para serem indexadas**: se conteúdo publicado há 2-3 semanas ainda não aparece no Google, o crawl budget pode estar sendo consumido por URLs de baixo valor.

**Relatório de crawl stats do Search Console mostrando muitas requisições em URLs de baixo valor**: se o Googlebot gasta a maioria dos rastreamentos em páginas de filtro, paginação ou parâmetros, há desperdício.

**Grande volume de "Descoberta, atualmente não indexada" no relatório de Páginas**, indica que o Google conhece as URLs mas não priorizou o rastreamento delas.

**Diferença grande entre páginas no sitemap e páginas indexadas**: se o sitemap tem 50 mil URLs e o Google indexou apenas 20 mil, há um gargalo de rastreamento ou qualidade.

### Como Otimizar o Crawl Budget

**Eliminar URLs de baixo valor**: bloquear parâmetros de busca interna, filtros sem volume de busca e variações de URL que geram conteúdo duplicado. Usar robots.txt, meta noindex ou canonical tags conforme o caso.

**Reduzir profundidade de clique**: páginas mais próximas da homepage são rastreadas com mais frequência. Reestruturar a [arquitetura](arquitetura-de-site-para-seo.md) para que conteúdo estratégico esteja a 2-3 cliques de profundidade.

**Melhorar a velocidade do servidor**: um servidor que responde rápido permite ao Googlebot rastrear mais páginas por visita. Otimizar TTFB (Time to First Byte) beneficia diretamente o crawl rate.

**Manter sitemaps XML precisos**: sitemaps atualizados e sem URLs com erro direcionam o Googlebot para onde ele deve ir, em vez de desperdiçar requisições em URLs problemáticas.

**Corrigir cadeias de redirecionamento**: cada 301 em cadeia consome uma requisição adicional de crawl. Redirecionar sempre para o destino final, eliminando intermediários.

**Eliminar links internos para 404**: cada link interno que aponta para uma página inexistente é um rastreamento desperdiçado e um beco sem saída para o Googlebot.

---

## 📑 Indexação: De Crawling para o Índice do Google

Depois de rastrear uma página, o Google decide se ela merece entrar no índice, a base de dados gigantesca de todas as páginas que podem aparecer nos resultados de busca. A indexação não é automática: o Google aplica critérios de qualidade, relevância e unicidade antes de incluir uma página.

### Como Funciona o Processo de Indexação

O pipeline de indexação envolve: renderização (o Google executa JavaScript e monta o DOM completo da página), extração de conteúdo (texto, imagens, links, dados estruturados), avaliação de qualidade (o conteúdo é útil, único e relevante?), e armazenamento no índice (com todos os sinais necessários para rankeamento futuro).

Fatores que influenciam a decisão de indexar: qualidade e unicidade do conteúdo (conteúdo duplicado ou thin content é frequentemente excluído), sinais de autoridade (páginas com backlinks e links internos têm maior probabilidade de indexação), [dados estruturados](schema-markup-e-dados-estruturados-para-seo.md) (ajudam o Google a entender o conteúdo com precisão) e status HTTP (páginas com erro 5xx ou soft 404 não são indexadas).

### Canonical Tags e Consolidação de Páginas

A tag canonical (`rel="canonical"`) indica ao Google qual é a versão "oficial" de uma página quando existem múltiplas URLs com conteúdo igual ou muito similar. É o mecanismo de consolidação que evita duplicação no índice.

Cenários comuns que exigem canonical: versões com e sem www (`www.site.com` e `site.com`), versões HTTP e HTTPS, parâmetros de URL que não alteram o conteúdo (`?utm_source=...`), paginação de conteúdo, e versões mobile e desktop em URLs separadas.

A canonical é uma sugestão ao Google, não uma ordem. O Google pode ignorar a canonical se considerar que a versão sugerida não é a melhor. Por isso, a canonical deve ser coerente com outros sinais: links internos, sitemap, hreflang e conteúdo da página devem todos apontar para a mesma versão preferida.

Erros comuns com canonical: canonical apontando para uma página com noindex (contradição), canonical apontando para uma URL 404, canonical bidirecional (página A aponta para B e B aponta para A), e ausência de canonical em páginas com parâmetros dinâmicos.

### Meta Robots e Noindex/Nofollow

A meta tag robots controla o comportamento do Google no nível da página individual:

**noindex**: instrui o Google a não incluir a página no índice. A página pode ser rastreada, mas não aparecerá nos resultados de busca. Usar para: páginas de agradecimento, páginas de login, conteúdo duplicado que não pode ser consolidado via canonical, landing pages de teste.

**nofollow**: instrui o Google a não seguir os links da página. Raramente útil como meta tag de página inteira. Mais comum como atributo em links individuais (`rel="nofollow"`) para links patrocinados ou de conteúdo gerado por usuários.

**A combinação noindex, follow**: permite que o Google rastreie os links da página (passando autoridade) sem indexar a página em si. Útil para páginas hub que existem apenas para distribuir link equity.

A diferença entre robots.txt e meta robots: robots.txt impede o rastreamento (o Googlebot nem acessa a página), enquanto meta robots permite o rastreamento mas controla a indexação. Para impedir que uma página apareça no Google, o caminho correto é meta noindex, não robots.txt, que pode bloquear o acesso à própria tag noindex.

---

## 🔧 Diagnóstico de Problemas de Indexação

Problemas de indexação são silenciosos: você publica conteúdo, o site parece funcionar normalmente, mas o Google simplesmente não mostra suas páginas nos resultados. Sem monitoramento ativo, esses problemas podem persistir por meses, desperdiçando investimento em conteúdo e link building.

### Google Search Console: Relatório de Cobertura

O relatório de Páginas (anteriormente chamado de Cobertura de Indexação) no Google Search Console é a ferramenta primária para diagnóstico. Ele classifica todas as URLs conhecidas pelo Google em quatro categorias:

**Válida (indexada)**: páginas que estão no índice e podem aparecer nos resultados.

**Válida com avisos**: páginas indexadas mas com potenciais problemas (ex: indexada apesar de bloqueada no robots.txt).

**Excluída**: páginas que o Google conhece mas decidiu não indexar. Os motivos são detalhados (noindex, canonical alternativa, conteúdo duplicado, etc.).

**Erro**: páginas com problemas técnicos que impedem a indexação (erro de servidor 5xx, erro de redirecionamento, URL bloqueada submetida).

A análise desse relatório revela a saúde real da indexação do site: quantas páginas estão indexadas vs. quantas deveriam estar, quais motivos de exclusão dominam e onde estão os gargalos técnicos.

### Páginas Descobertas Mas Não Indexadas

"Descoberta, atualmente não indexada" é uma das mensagens mais comuns e mais frustrantes do Search Console. Significa que o Google sabe que a URL existe mas ainda não a rastreou ou decidiu não priorizá-la.

Causas possíveis: crawl budget insuficiente para o volume de URLs do site, conteúdo percebido como de baixo valor (thin content), site com autoridade ainda em construção (sites novos enfrentam isso naturalmente), e sobrecarga de URLs de baixo valor competindo pelo crawl budget.

Ações para resolver: melhorar a qualidade do conteúdo das páginas afetadas, aumentar links internos apontando para elas, submeter URLs manualmente via "Solicitar indexação" no Search Console (útil para páginas prioritárias), e otimizar o crawl budget eliminando URLs de baixo valor que competem por atenção.

### Erros de Servidor e Redirects

**Erros 5xx (Server Error)** indicam que o servidor falhou ao responder à requisição do Googlebot. Erros frequentes de servidor prejudicam a percepção de confiabilidade do site e podem levar o Google a reduzir a frequência de rastreamento.

**Erros de redirecionamento**: loops (página A redireciona para B que redireciona para A), cadeias longas (301 → 301 → 301 → destino final), e uso incorreto de 302 (temporário) onde deveria ser 301 (permanente). Cada um desperdiça crawl budget e pode impedir a indexação correta da página de destino.

**Soft 404**, páginas que retornam status HTTP 200 (OK) mas exibem conteúdo de "página não encontrada". O Google detecta soft 404s e os trata como erros, a página não é indexada, mas o servidor desperdiçou crawl budget ao servir uma resposta "válida" para uma página sem conteúdo real.

A TRIWI monitora a saúde de indexação como parte do escopo de "Aumento das Palavras Indexadas no Google", a 8ª das 12 entregas da [metodologia](../triwi/metodologia-triwi.md), com acompanhamento mensal. Esse monitoramento contínuo permite identificar regressões de indexação antes que se tornem problemas de rankeamento: uma queda de 500 páginas indexadas em um mês pode significar um robots.txt mal configurado, uma canonical errada em massa ou uma instabilidade de servidor que precisa de correção imediata.

---

## 📩 Próximos Passos

Crawling e indexação são os processos invisíveis que determinam se o seu conteúdo sequer participa do jogo do rankeamento. Um site com milhares de páginas bem escritas mas mal indexadas é como uma biblioteca com livros trancados em uma sala sem porta, o conteúdo existe, mas ninguém consegue acessá-lo.

Se sua empresa quer garantir que cada página relevante do site seja rastreada, indexada e elegível para rankear, conheça a [Metodologia TRIWI](https://triwi.com.br/metodologia-triwi/) e entenda como o monitoramento contínuo de indexação se integra às 300+ atividades que sustentam resultados de longo prazo.

Explore as páginas relacionadas:

- 🛠️ [SEO Técnico](README.md): O guia completo de SEO técnico: pilares, auditoria e otimização enterprise.
- 🔎 [Como Funciona o Google](../fundamentos-de-seo/como-funciona-o-google-rastreamento-indexacao-e-rankeamento.md): Rastreamento, indexação e rankeamento: o pipeline completo.
- 🏗️ [Arquitetura de Site para SEO](arquitetura-de-site-para-seo.md): Como a estrutura do site impacta a eficiência do rastreamento.
- 📱 [Velocidade do Site](velocidade-do-site-impacto-no-seo-e-nas-conversoes.md): Performance de servidor e seu impacto no crawl rate.
- 📈 [Ferramentas de SEO](../metricas-e-ferramentas/ferramentas-de-seo-guia-completo-das-melhores-ferramentas.md): Google Search Console e outras ferramentas essenciais para monitoramento.
- 🛡️ [Por Que a TRIWI](../triwi/por-que-a-triwi.md): Diferenciais, comparativos e resultados comprovados.

**Seu conteúdo está chegando ao índice do Google?** [Fale com a TRIWI](https://triwi.com.br/porque-a-triwi/).

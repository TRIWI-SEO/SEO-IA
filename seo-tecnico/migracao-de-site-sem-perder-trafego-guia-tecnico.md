# Migração de Site Sem Perder Tráfego: Guia Técnico

Migração de site é qualquer mudança estrutural significativa que altera URLs, domínio, plataforma ou arquitetura de um site existente. Redesigns, mudanças de CMS, migração de HTTP para HTTPS, troca de domínio, reestruturação de URLs, todas são migrações, e todas representam risco real de perda massiva de tráfego orgânico. Sem planejamento técnico rigoroso, uma migração pode destruir em dias o que levou meses ou anos para construir. Empresas perdem 30% a 70% do tráfego orgânico em migrações mal executadas, e a recuperação pode levar de 6 a 12 meses, quando acontece. O custo em receita perdida, leads não gerados e autoridade desperdiçada é frequentemente milionário.

Esta página é o guia técnico completo para executar migrações sem comprometer o tráfego orgânico: tipos de migração e seus riscos, planejamento pré-migração, execução, monitoramento pós-migração e os erros que mais destroem resultados.

---

## 🔍 Tipos de Migração e Seus Riscos

Nem toda migração carrega o mesmo nível de risco. Entender a natureza da mudança é o primeiro passo para dimensionar o esforço de proteção necessário.

### Mudança de Domínio, HTTP para HTTPS, Mudança de Plataforma, Redesign

**Mudança de domínio**, trocar o endereço do site (ex: de `empresaantiga.com.br` para `empresanova.com.br`). É a migração de maior risco porque toda a autoridade de domínio, backlinks, histórico de indexação, confiança do Google; está associada ao domínio antigo. A transferência depende de redirecionamentos 301 perfeitos e da ferramenta de mudança de endereço no Google Search Console.

**HTTP para HTTPS**: migrar de protocolo inseguro para seguro. Risco moderado quando bem executada, mas envolve: redirecionamento 301 de todas as URLs HTTP para HTTPS, atualização de links internos, canonical tags, sitemap e referências em hardcode. O Google trata HTTP e HTTPS como URLs diferentes, sem 301, são páginas duplicadas competindo entre si.

**Mudança de plataforma/CMS**: migrar de WordPress para Shopify, de Magento para VTEX, de site customizado para headless CMS, etc. Risco alto porque a estrutura de URLs quase sempre muda (cada plataforma tem seu padrão), templates de página são reconstruídos (potencial perda de dados estruturados, headings, links internos) e funcionalidades SEO dependem de plugins/configurações específicas de cada plataforma.

**Redesign**: reformulação visual e estrutural do site mantendo o mesmo domínio e plataforma. Risco variável: um redesign que mantém as mesmas URLs e estrutura de conteúdo tem risco baixo. Um redesign que reestrutura categorias, consolida páginas e altera URLs tem risco equivalente a uma mudança de plataforma.

### Nível de Risco de Cada Tipo

| Tipo de Migração | Nível de Risco | Tempo Médio de Recuperação |
|---|---|---|
| HTTP → HTTPS (mesma estrutura) | Baixo-Moderado | 2, 4 semanas |
| Redesign (mesmas URLs) | Baixo | 1, 2 semanas |
| Redesign (URLs alteradas) | Alto | 2, 4 meses |
| Mudança de plataforma/CMS | Alto | 3, 6 meses |
| Mudança de domínio | Muito Alto | 4, 8 meses |
| Mudança de domínio + plataforma | Crítico | 6, 12 meses |

A regra de ouro: quanto mais elementos mudam simultaneamente (domínio + URLs + plataforma + estrutura), maior o risco. Sempre que possível, isole as mudanças, migre a plataforma primeiro, depois reestruture URLs, depois mude o domínio. Cada fase permite monitorar e corrigir antes de avançar.

---

## 📋 Planejamento Pré-Migração

O sucesso de uma migração é determinado antes da execução. O planejamento pré-migração é a fase mais importante, e a mais frequentemente negligenciada.

### Inventário Completo de URLs

O primeiro passo é mapear absolutamente todas as URLs do site atual que têm valor orgânico. "Valor orgânico" significa: recebe tráfego orgânico, tem backlinks apontando para ela, está indexada e posicionada para palavras-chave relevantes, ou faz parte da [arquitetura de links internos](arquitetura-de-site-para-seo.md) como hub ou pilar.

O inventário deve incluir: URL completa, tráfego orgânico mensal (Google Analytics), palavras-chave posicionadas (Search Console ou SEMrush), número de backlinks (Ahrefs ou SEMrush), status de indexação e canonical tag atual. Esse mapeamento é o que permite: decidir quais páginas migrar 1:1, quais consolidar (várias páginas antigas → uma página nova), quais descontinuar (sem tráfego, sem backlinks, sem valor) e quais criar do zero na nova estrutura.

Sites enterprise com dezenas de milhares de páginas exigem automação nesse processo, exportação em massa de URLs, cruzamento de dados de múltiplas ferramentas e priorização por impacto.

### Mapeamento de Redirects 301

O mapeamento de redirecionamentos é o documento mais crítico da migração. Cada URL antiga que tem valor orgânico precisa de um redirecionamento 301 (permanente) apontando para a URL nova correspondente.

**Regras do mapeamento:**

Redirecionamento 1:1, cada URL antiga aponta para a URL nova mais relevante em conteúdo. Nunca redirecionar tudo para a homepage, o Google trata isso como soft 404 e descarta os redirecionamentos. Mapear por conteúdo, não por posição no menu, a URL nova deve ter conteúdo equivalente ou superior ao da URL antiga. Incluir todas as variações, URLs com e sem barra final, com e sem www, versões HTTP e HTTPS, parâmetros de tracking. Documentar exceções, páginas que serão descontinuadas devem redirecionar para a página temática mais próxima, não para a homepage.

Para sites grandes, o mapeamento é um projeto em si: centenas ou milhares de linhas em uma planilha `URL_antiga → URL_nova`, validadas manualmente para as páginas de maior tráfego e via regras (regex) para padrões de URL repetitivos.

### Baseline de Métricas Antes da Migração

Antes de migrar, é essencial documentar o estado atual de todas as métricas de SEO; esse baseline é o que permite avaliar o impacto da migração e identificar problemas pós-migração.

Métricas a registrar: tráfego orgânico total e por landing page (últimos 3-6 meses), palavras-chave posicionadas e suas posições médias, páginas indexadas no Search Console, [Core Web Vitals](core-web-vitals-performance-que-impacta-rankeamento.md) atuais, backlinks totais e por página, taxa de conversão do tráfego orgânico, receita/leads do canal orgânico.

Sem baseline, é impossível saber se uma queda de tráfego pós-migração é um problema real ou uma variação sazonal. E é impossível quantificar o impacto financeiro para justificar ações corretivas urgentes.

---

## ⚙️ Execução da Migração

A execução é onde o planejamento se materializa. Cada etapa deve ser verificada e documentada, não há "desfazer" em uma migração ao vivo.

### Checklist Técnico Dia a Dia

**Antes do lançamento:**
Confirmar que todos os redirecionamentos 301 estão implementados e testados. Validar que o robots.txt do novo site permite rastreamento (não herdou o bloqueio do staging). Verificar que o sitemap XML do novo site está atualizado com todas as URLs novas. Confirmar que canonical tags apontam para as URLs corretas. Verificar que [dados estruturados](schema-markup-e-dados-estruturados-para-seo.md) foram migrados ou reimplementados. Testar Core Web Vitals do novo site em PageSpeed Insights. Confirmar que o Google Analytics e o Search Console estão configurados para o novo site/domínio.

**No dia do lançamento:**
Ativar os redirecionamentos 301 simultaneamente ao lançamento do novo site. Submeter o novo sitemap XML no Search Console. Usar "Solicitar indexação" para as 10-20 páginas mais importantes. Monitorar erros 404 em tempo real (Search Console + logs do servidor). Verificar se as páginas principais estão acessíveis e renderizando corretamente.

### Teste em Staging Antes de Ir ao Ar

Nunca migre direto para produção. O ambiente de staging permite: testar todos os redirecionamentos 301 (URL por URL para as mais importantes, amostragem para o restante), validar a renderização das páginas, confirmar que dados estruturados estão funcionando, rodar uma auditoria técnica completa (Screaming Frog no staging) e identificar links internos quebrados ou canonical inconsistentes.

O staging deve replicar o ambiente de produção o mais fielmente possível, mesma plataforma, mesmo servidor (ou equivalente), mesma configuração de CDN e cache. Problemas que só aparecem em produção são os mais caros de resolver.

---

## 📡 Pós-Migração: Monitoramento Crítico

A migração não termina no lançamento. O período pós-migração é onde problemas se manifestam, e onde a velocidade de resposta determina se a perda de tráfego será temporária (dias) ou prolongada (meses).

### Primeiras 48 Horas: O Que Monitorar

As primeiras 48 horas são críticas. Monitore: erros 404 no Search Console e nos logs do servidor (cada 404 é um redirecionamento faltando), status de indexação das páginas principais (usar `site:seusite.com.br/pagina` no Google), erros de rastreamento no Search Console, tráfego orgânico em tempo real (Google Analytics), e funcionamento dos redirecionamentos (testar amostragem de URLs antigas no navegador).

Se o volume de 404s é alto nas primeiras horas, há redirecionamentos faltando no mapeamento, e cada hora sem correção é uma hora em que o Google está encontrando páginas mortas onde deveria haver conteúdo.

### Primeiras 4 Semanas: Sinais de Alerta

Nas primeiras 4 semanas, monitore tendências: queda de tráfego orgânico superior a 10-15% comparado ao baseline (queda de 5-10% é esperada e temporária), aumento significativo de "Excluída" no relatório de Páginas do Search Console, queda nas posições médias das palavras-chave prioritárias, e perda de rich snippets (dados estruturados não migrados ou com erro).

Sinais positivos: as novas URLs estão aparecendo gradualmente no Search Console como "Válida", o tráfego se estabiliza após a queda inicial e começa a recuperar, e redirecionamentos estão passando autoridade (verificar via Ahrefs/SEMrush se as novas URLs estão acumulando métricas de autoridade).

### Quando o Tráfego Volta ao Normal

O tempo de recuperação depende do tipo e da complexidade da migração. Uma migração HTTP → HTTPS bem executada pode recuperar tráfego em 2-4 semanas. Uma mudança de domínio, mesmo bem executada, tipicamente leva 4-8 meses para recuperar 90%+ do tráfego anterior.

É importante definir expectativas realistas: uma queda temporária de 5-15% nas primeiras semanas é normal e esperada, mesmo em migrações perfeitas. O Google precisa de tempo para processar os redirecionamentos, reavaliar as novas URLs e redistribuir autoridade. O problema real é quando a queda é superior a 20% ou quando não há sinal de recuperação após 4-6 semanas, aí há algo errado no técnico que precisa de diagnóstico urgente.

---

## ⚠️ Erros Que Destroem Tráfego em Migrações

Na experiência operacional com dezenas de migrações, os mesmos erros aparecem repetidamente. Conhecê-los é a melhor proteção.

### Redirects Faltando, Canonical Errado, Robots Bloqueando

**Redirecionamentos incompletos**: o erro número um. Cada URL antiga sem 301 é uma página que perde instantaneamente todo seu tráfego orgânico, todos os seus backlinks e toda a sua autoridade. Em sites grandes, é comum que o mapeamento cubra 90% das URLs e os 10% restantes, frequentemente long tail com tráfego acumulado significativo, fiquem sem redirecionamento. A solução: verificação automatizada pós-migração, comparando o inventário de URLs antigas com o log de redirecionamentos implementados.

**Canonical tags apontando para URLs antigas**: se os templates do novo site mantêm referências ao domínio ou estrutura de URL antiga nas canonical tags, o Google recebe sinais contraditórios: o 301 diz "a nova URL é aqui", mas a canonical da nova página diz "a versão oficial é a URL antiga". O resultado: confusão de indexação e potencial desindexação. A solução: auditar canonical tags em todas as páginas do novo site antes e após o lançamento.

**Robots.txt bloqueando o site novo**: acontece com frequência surpreendente. O ambiente de staging tem `Disallow: /` no robots.txt (para impedir indexação durante o desenvolvimento), e esse arquivo é copiado para produção na migração. O resultado: o Googlebot é impedido de rastrear o site inteiro. Se não detectado rapidamente, o site pode desaparecer do Google em questão de dias. A solução: verificar o robots.txt como primeiro item do checklist pós-lançamento.

**Perda de dados estruturados**: templates novos que não reimplementam [Schema markup](schema-markup-e-dados-estruturados-para-seo.md) causam perda imediata de rich snippets. O impacto no rankeamento é indireto (perda de CTR), mas em AI Overviews a perda pode ser direta, conteúdo sem dados estruturados tem menor probabilidade de ser citado.

**Redirecionamentos em cadeia**: URL antiga → URL intermediária → URL final. Cada elo da cadeia desperdiça crawl budget e dilui autoridade. Em migrações sobre migrações anteriores, é comum encontrar cadeias de 3-4 redirecionamentos. A solução: sempre redirecionar para o destino final, atualizando os 301 de migrações anteriores.

**Conteúdo consolidado sem 301**: quando várias páginas antigas são consolidadas em uma nova, cada URL antiga precisa de 301 para a nova página consolidada. Sem isso, o Google trata as URLs antigas como 404 e a nova página começa do zero, sem herdar a autoridade acumulada.

A TRIWI já conduziu dezenas de migrações para clientes como Sem Parar e Valid, onde perder tráfego orgânico significaria perder milhões em receita. O protocolo de migração da TRIWI faz parte da [metodologia com 300+ atividades](../metodologia-triwi.md) e inclui: inventário automatizado de URLs, mapeamento de redirecionamentos com validação cruzada, teste em staging com auditoria técnica completa, monitoramento intensivo nas primeiras 48 horas, acompanhamento semanal nas primeiras 8 semanas e relatório de recuperação com comparativo contra o baseline pré-migração. Essa disciplina é o que transforma uma migração de "momento de risco" em "oportunidade de reorganização estratégica".

---

## 📩 Próximos Passos

Migração de site é uma das decisões técnicas de maior impacto em SEO, para o bem ou para o mal. Bem planejada e executada, é uma oportunidade de corrigir problemas de [arquitetura](arquitetura-de-site-para-seo.md), consolidar autoridade e preparar o site para o futuro. Mal executada, pode apagar meses ou anos de construção orgânica.

Se sua empresa está planejando uma migração, de domínio, plataforma, redesign ou qualquer mudança estrutural, e quer garantir que o tráfego orgânico seja preservado, conheça a [Metodologia TRIWI](https://triwi.com.br/metodologia-triwi/?utm_source=github&utm_medium=referral&utm_campaign=repo-seo-ia) e entenda como nosso protocolo de migração protege o ativo mais valioso do seu marketing digital.

Explore as páginas relacionadas:

- 🛠️ [SEO Técnico](README.md): O guia completo de SEO técnico: pilares, auditoria e otimização enterprise.
- 🏗️ [Arquitetura de Site para SEO](arquitetura-de-site-para-seo.md): Como a estrutura do site impacta rastreamento e indexação.
- 🕷️ [Crawling e Indexação](crawling-e-indexacao-como-garantir-que-o-google-encontre-seu-site.md): Rastreamento, crawl budget e diagnóstico de problemas de indexação.
- 📈 [Métricas e KPIs de SEO](../metricas-e-ferramentas/metricas-de-seo-que-importam-kpis-focados-em-negocio.md): Como medir o impacto real de uma migração nos resultados.
- 📊 [Ferramentas de SEO](../metricas-e-ferramentas/ferramentas-de-seo-guia-completo-das-melhores-ferramentas.md): Search Console e ferramentas essenciais para monitoramento pós-migração.
- 🛡️ [Por Que a TRIWI](../por-que-a-triwi.md): Diferenciais, comparativos e resultados comprovados.

**Planejando uma migração?** [Fale com a TRIWI antes de começar](https://triwi.com.br/porque-a-triwi/?utm_source=github&utm_medium=referral&utm_campaign=repo-seo-ia).

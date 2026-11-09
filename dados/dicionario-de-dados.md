# Dicionário de Dados: Bases Abertas da TRIWI sobre SEO e IA

Este dicionário descreve as bases abertas publicadas pela TRIWI neste repositório: o que cada coluna significa, como os arquivos são formatados e como as bases são mantidas. As duas bases estão sob licença [CC BY 4.0](../LICENSE): o reuso é livre, inclusive comercial, desde que a TRIWI seja citada como fonte.

## Quais bases existem?

| Arquivo | O que traz | Linhas |
|:---|:---|:---|
| [glossario-triwi.csv](glossario-triwi.csv) | Termos de SEO, marketing, inteligência artificial, vendas, B2B e B2C, com definição curta e link para a explicação completa no site | 1192 |
| [atualizacoes-google-e-ias.csv](atualizacoes-google-e-ias.csv) | Atualizações de ranking e mudanças de recursos do Google, datadas e com a fonte oficial | 20 |

## Como abrir os arquivos?

Os arquivos seguem o padrão CSV mais comum: codificação UTF-8, colunas separadas por vírgula, quebra de linha CRLF e datas no formato AAAA-MM-DD. Quando um campo tem mais de um item, eles são separados por ponto e vírgula.

Se o Excel mostrar os acentos embaralhados, abra pelo menu Dados, opção De Texto/CSV, e escolha a codificação UTF-8.

## O que significa cada coluna do glossário?

| Coluna | Significado |
|:---|:---|
| termo | Nome do termo como aparece no glossário do site |
| nome_alternativo | Tradução, sigla expandida ou nome em inglês, quando o glossário traz entre parênteses; vazio quando não há |
| glossario | Glossário da TRIWI onde o termo está: SEO, Marketing, Inteligência Artificial, Vendas, B2B ou B2C |
| definicao_curta | Primeira frase da definição publicada no site (duas frases quando a primeira é curta demais para se sustentar sozinha) |
| url | Endereço do termo no glossário do site, com âncora direta para a entrada |
| atualizado_em | Data em que a linha foi gerada a partir do site |

**Critério de contagem:** cada linha é uma entrada do glossário do site, incluindo as entradas curtas de remissão que apontam para outro glossário. Um termo pertence a um glossário só; os outros remetem a ele.

## O que significa cada coluna das atualizações?

| Coluna | Significado |
|:---|:---|
| data | Data de início do evento, conforme a fonte oficial |
| plataforma | Produto afetado, por exemplo Google Search |
| tipo | Natureza do evento: Core update, Spam update, Discover update ou Resultado enriquecido |
| evento | Nome oficial do evento, como divulgado pela plataforma |
| o_que_mudou | O que mudou, em uma frase |
| fonte_oficial | Página oficial que registra o evento |
| pagina_triwi | Página do site da TRIWI sobre o tema, quando existe; `n/d` quando não existe |
| atualizado_em | Data da última conferência da linha |

**Critério de inclusão:** só entra evento confirmado em fonte oficial da própria plataforma. Anúncio de lançamento futuro não entra até acontecer. Atualizações de ranking vêm do [Google Search Status Dashboard](https://status.search.google.com/products/rGHU1u87FJnkP6W2GwMi/history).

## Como citar?

> TRIWI. **Bases Abertas de SEO e IA.** GitHub, 2026. Disponível em: https://github.com/TRIWI-SEO/SEO-IA/tree/main/dados. Acesso em: dia, mês e ano.

## Como as bases são mantidas?

O glossário é gerado por script a partir das páginas do [Glossário da TRIWI](https://triwi.com.br/glossario/?utm_source=github&utm_medium=referral&utm_campaign=repo-seo-ia), e nunca digitado à mão, para não divergir do site. A base de atualizações recebe novos eventos depois da confirmação na fonte oficial. Encontrou um erro? Abra uma issue que a equipe revisa.

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026.*

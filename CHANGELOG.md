# Changelog

## 0.2.0 - Inteligência local de recomendação

### Adicionado

* Criada camada local de recomendação para produtos e ofertas.
* Adicionado arquivo `recommendations.ts` para centralizar a lógica de diagnóstico.
* Adicionado Diagnóstico Garimpa AI na tela de comparativo.
* Adicionado Diagnóstico Garimpa AI compacto na tela de produto.
* Adicionadas tags inteligentes nos cards do Dashboard.
* Adicionada indicação de formatos recomendados no Gerador de Anúncios.
* Adicionada sugestão de canais no Gerador com base na oferta selecionada.

### Melhorado

* O comparativo passou a explicar melhor por que uma oferta é sugerida.
* A tela de produto passou a mostrar potencial, risco e canais recomendados.
* O Dashboard passou a exibir sinais rápidos de oportunidade nos cards.
* O Gerador passou a destacar formatos mais adequados para cada produto/oferta.
* A experiência geral ficou mais próxima de um assistente de decisão para afiliados.

### Técnico

* A lógica de recomendação ainda é local, baseada em dados mockados ou persistidos no navegador.
* Nenhuma API externa foi adicionada nesta etapa.
* Nenhuma integração com OpenAI, Supabase, autenticação ou marketplace real foi incluída.
* A estrutura foi preparada para futura evolução com dados reais e IA generativa.

### Critérios considerados

A recomendação local considera, quando disponível:

* preço;
* avaliação;
* número de avaliações;
* vendas aproximadas;
* comissão estimada;
* disponibilidade;
* categoria do produto;
* ponto forte;
* ponto de atenção;
* público ideal;
* melhor oferta calculada.

### Status

Primeira versão da inteligência local implementada e validada no protótipo.

## 0.1.6 - Polimento visual do MVP

### Adicionado

- Cards de resumo no Dashboard.
- Melhor organização dos filtros de marketplace, categoria, nota, comissão e ordenação.
- Fallback visual para imagens ausentes ou quebradas.
- Melhor hierarquia visual nos cards de produto.
- Melhorias visuais na tela de produto.
- Melhorias visuais na tela de comparativo.
- Melhorias visuais no gerador multicanal.
- Ajustes visuais na tela de produtos salvos e área administrativa.

### Melhorado

- O Dashboard passou a se apresentar como uma central de oportunidades.
- Os cards de produto ficaram mais claros e profissionais.
- A identidade visual ficou mais consistente entre as telas.
- O uso de azul escuro, laranja, branco e cinza claro foi refinado.
- A experiência geral ficou mais próxima de um produto SaaS.

### Técnico

- Mantida a lógica atual de produtos, ofertas, comparativo e gerador.
- Não foram adicionadas APIs, autenticação, Supabase ou pagamentos nesta etapa.
- As mudanças foram focadas em UX, UI e responsividade.

### Próximo passo

- Validar o fluxo completo após o polimento.
- Corrigir eventuais problemas visuais ou funcionais encontrados.
- Planejar a próxima fase: integração com dados reais/APIs oficiais.

## 0.1.5 - Evolução do gerador multicanal de anúncios

### Adicionado

- Novos formatos de geração de conteúdo para WhatsApp, Telegram, Instagram, Stories, Reels e TikTok.
- Formatos premium para prompts de vídeo com IA.
- Geração de conteúdo em blocos, como gancho, legenda, roteiro, CTA, hashtags e prompt IA.
- Resumo da oferta selecionada dentro do gerador.
- Botão para copiar cada bloco individualmente.
- Botão para copiar todo o conteúdo gerado.

### Melhorado

- O gerador passou a usar melhor os dados da oferta selecionada.
- Os textos gerados ficaram mais específicos para cada canal.
- O fluxo de geração agora considera produto base, marketplace, preço, avaliação, vendas aproximadas, comissão e ponto de atenção.
- A interface do gerador ficou mais organizada para múltiplos formatos.

### Técnico

- Refatorado `adTemplates.ts` para retornar blocos estruturados de conteúdo.
- Atualizado `AdGenerator.tsx` para renderizar múltiplos blocos por formato.
- Mantida a geração local com dados mockados, sem integração real com IA externa nesta etapa.

### Próximo passo

- Revisar visual e usabilidade do gerador.
- Planejar futura integração com IA real e APIs oficiais de marketplaces.

## 0.1.4 - Correção da rota de comparativo e lógica de ofertas

### Corrigido

- Corrigida a rota `/produto/:id/comparativo`, que estava exibindo a tela de detalhes do produto em vez da tela de comparação.
- Separada a rota pai do produto da tela de detalhes usando uma rota index dedicada.
- A tela de comparativo passou a renderizar corretamente as ofertas por marketplace.
- Corrigida inconsistência visual em que o card/tela podia exibir marketplace de uma oferta e preço de outra.

### Adicionado

- Tela de comparativo vertical entre marketplaces.
- Seletor de marketplaces para comparação.
- Destaques para melhor preço, melhor avaliação, melhor prova social, melhor entrega, melhor comissão e melhor opção geral.
- Resumo de análise com recomendação da melhor oferta.
- Dados mockados mais realistas para ofertas por marketplace.

### Técnico

- Reforçada a separação entre produto base e oferta de marketplace.
- `Product` representa o produto principal.
- `Offer` representa a oferta específica em Amazon, Mercado Livre, Shopee ou Magalu.
- A melhor oferta deve ser calculada em runtime, e não depender apenas de um campo fixo no produto.

### Próximo passo

- Melhorar o Gerador de Anúncios para usar a oferta selecionada no comparativo e gerar textos mais chamativos, claros e adequados para cada canal.

## 0.1.3 - Validação funcional do protótipo local

### Validado

- Protótipo executado localmente após correção do store.
- Páginas Produtos e Salvos abriram sem erro.
- Lógica principal do app validada.
- Gerador de anúncios funcionando em nível inicial.
- Área admin funcionando em nível inicial.

### Identificado

- Necessidade de ajustes visuais.
- Necessidade de melhoria nos textos do Gerador de Anúncios.
- Próxima etapa será refinamento de UX e conteúdo.

## 0.1.2 - Correção inicial do protótipo local

### Corrigido

- Corrigido erro de loop infinito de renderização nas páginas Produtos e Salvos.
- Removido uso problemático de `useSyncExternalStore` com leitura direta de `localStorage`.
- Ajustada a leitura dos dados mockados/persistidos para evitar snapshots instáveis.
- Melhorado o componente `ProductCard` com cálculos memoizados.
- Adicionado `package-lock.json` para permitir instalação e execução do projeto com npm.

### Técnico

- O erro era causado por snapshots que retornavam novos arrays a cada renderização.
- O problema impactava componentes como `ProductCard` e a página de produtos salvos.
- A correção foi aplicada no repositório técnico `garimpa-ai-hub`.

### Status

- Protótipo rodando localmente.
- Próxima etapa técnica: revisar telas restantes e decidir estratégia de migração para `garimpa.ai`.

## 0.1.1 - Validação local do protótipo

### Adicionado

- Protótipo Lovable clonado e executado localmente.
- Validação inicial das telas principais.
- Registro de ambiente local com Node.js, npm e Vite.

## 0.1.0 - Protótipo inicial

### Adicionado

- Definição inicial do produto Garimpa AI.
- Escopo da versão 1.
- Protótipo inicial criado com Lovable.
- Landing page pública.
- Dashboard com produtos sugeridos.
- Busca e filtros.
- Comparativo entre marketplaces.
- Gerador de anúncios mockado.
- Produtos salvos.
- Área admin inicial.
- Páginas de Termos e Privacidade.
## 005 — Corrigir store local antes de evoluir o protótipo

**Data:** 2026-06-08

### Contexto

Durante a validação local do protótipo gerado pelo Lovable, as páginas **Produtos** e **Salvos** apresentaram erro de carregamento.

No console do navegador, foram identificadas mensagens como:

```text
Maximum update depth exceeded
The result of getSnapshot should be cached to avoid an infinite loop
```

O problema indicava um loop infinito de renderização no React.

### Decisão

Foi decidido remover o uso problemático de `useSyncExternalStore` para leitura direta de dados do `localStorage` no store local do protótipo.

A implementação foi substituída por uma abordagem mais simples, usando `useState`, `useEffect` e um mecanismo interno de notificação para atualizar os dados locais.

### Motivo

O `useSyncExternalStore` exige que o `getSnapshot` retorne um valor estável quando os dados não mudam.

Como a leitura do `localStorage` usava `JSON.parse`, novos arrays eram criados a cada chamada. Mesmo com o mesmo conteúdo, o React interpretava esses arrays como novos valores, causando renderizações repetidas e o loop infinito.

### Impacto

Com a correção:

* as páginas **Produtos** e **Salvos** deixaram de quebrar por loop de renderização;
* o protótipo local ficou mais estável para validação;
* a lógica de persistência local ficou mais simples para a fase de MVP;
* a futura migração para Supabase ficou mais clara, pois o `localStorage` será tratado apenas como solução temporária do protótipo.

### Repositório relacionado

A correção foi aplicada no repositório técnico:

```text
garimpa-ai-hub
```

O repositório principal `garimpa.ai` registra esta decisão para manter o histórico técnico do projeto.

### Status

Decisão aplicada no protótipo local e registrada como referência para as próximas etapas de desenvolvimento.

## 006 — Separar produto base de oferta por marketplace

**Data:** 2026-06-14

### Contexto

A proposta do Garimpa AI exige comparar o mesmo produto, ou produtos equivalentes, em diferentes marketplaces.

Durante os testes, foi identificado que alguns componentes misturavam dados de fontes diferentes, como exibir a tag de um marketplace e o preço de outro.

### Decisão

Foi reforçada a separação entre:

- **Produto base:** representa a ideia principal do produto.
- **Oferta de marketplace:** representa uma oferta específica daquele produto em Amazon, Mercado Livre, Shopee, Magalu ou outro marketplace.

### Motivo

Essa separação é necessária para:

- comparar ofertas entre marketplaces;
- calcular a melhor opção em runtime;
- filtrar oportunidades pelos marketplaces usados pelo usuário;
- preparar o projeto para futuras APIs oficiais;
- evitar inconsistências como preço de um marketplace e tag de outro.

### Impacto

A lógica do dashboard, dos cards e do comparativo deve sempre usar dados de uma oferta específica ao exibir marketplace, preço, avaliação, vendas, comissão e disponibilidade.

O campo `bestMarketplace` do produto base passa a ser considerado apenas legado/mock, e não deve ser usado como fonte principal para decisões de comparação.

### Status

Decisão aplicada na lógica inicial do protótipo e registrada para orientar as próximas evoluções.

## 007 — Evoluir o gerador para conteúdo multicanal estruturado

**Data:** 2026-06-15

### Contexto

O Gerador de Anúncios inicialmente produzia textos simples em poucos formatos, como WhatsApp, Instagram, Reels e Stories.

Com a evolução do Garimpa AI, o gerador passou a precisar atender diferentes canais de divulgação, como WhatsApp, Telegram, Instagram, TikTok e formatos premium para prompts de vídeo com IA.

### Decisão

Foi decidido refatorar o gerador para trabalhar com blocos estruturados de conteúdo.

Em vez de retornar apenas um texto único, a função de geração passa a produzir blocos como:

- Gancho;
- Legenda;
- Roteiro;
- Texto na tela;
- CTA;
- Hashtags;
- Prompt para vídeo IA.

### Motivo

Essa estrutura permite adaptar melhor o conteúdo a cada canal e deixa o sistema preparado para futuras integrações com IA real.

### Impacto

O gerador passa a ser mais flexível, reutilizável e preparado para novos formatos de conteúdo.

Também fica mais fácil permitir que o usuário copie partes específicas do conteúdo gerado.

### Status

Decisão aplicada no protótipo local.
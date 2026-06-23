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

## 008 — Polimento visual do MVP antes de integrar APIs

**Data:** 2026-06-17

### Contexto

Após a implementação da lógica principal do Garimpa AI, o MVP já possuía:

* listagem de produtos;
* filtros por marketplace;
* comparação entre ofertas;
* melhor opção sugerida;
* geração multicanal de anúncios;
* área administrativa simples;
* produtos salvos.

Apesar da lógica estar funcional, a interface ainda precisava transmitir mais confiança, clareza e profissionalismo para se aproximar da experiência esperada de um produto SaaS.

### Decisão

Foi decidido realizar uma fase de polimento visual e UX antes de avançar para integrações mais complexas, como APIs oficiais de marketplaces, autenticação, Supabase ou IA real.

A Fase 1 de polimento visual teve foco em:

* melhorar a landing page;
* transformar o dashboard em uma central de oportunidades;
* melhorar a hierarquia visual dos cards;
* corrigir imagens quebradas com fallback visual;
* melhorar a tela de comparativo;
* melhorar a apresentação do gerador multicanal;
* manter a identidade visual baseada em azul escuro, laranja, branco e cinza claro.

### Motivo

Antes de integrar dados reais, o MVP precisa demonstrar valor de forma clara.

A decisão de polir a interface antes das APIs ajuda a:

* validar melhor a experiência do usuário;
* tornar o projeto mais apresentável para portfólio;
* facilitar demonstrações futuras;
* reduzir a percepção de protótipo inacabado;
* melhorar a clareza do fluxo principal;
* evitar adicionar complexidade sobre uma interface ainda pouco madura.

### Direção visual adotada

A identidade visual foi mantida com:

* azul escuro como cor principal, transmitindo confiança, tecnologia e análise;
* laranja como cor de ação para CTAs e destaques;
* branco e cinza claro como base de leitura;
* verde discreto para oportunidades, sucesso e melhor opção;
* amarelo discreto para alertas e pontos de atenção.

A intenção é transmitir uma experiência moderna, limpa, confiável e profissional, evitando aparência de site promocional agressivo.

### Impacto

A interface passou a comunicar melhor a proposta do Garimpa AI:

* encontrar produtos com potencial;
* comparar marketplaces;
* escolher a melhor oferta;
* gerar conteúdos prontos para divulgação.

O dashboard ganhou mais aparência de ferramenta analítica, os cards ficaram mais informativos e o fluxo principal ficou mais consistente visualmente.

### Fora do escopo

Nesta fase, não foram incluídos:

* APIs reais de marketplaces;
* autenticação;
* Supabase;
* pagamentos;
* integração com OpenAI API;
* geração real de imagens;
* geração real de vídeos;
* publicação automática em redes sociais.

### Status

Decisão aplicada no MVP e validada localmente.

## 009 — Criar camada local de recomendação

**Data:** 2026-06-22

### Contexto

Após a criação do comparativo entre marketplaces e do gerador multicanal de anúncios, o Garimpa AI passou a precisar explicar melhor por que uma oferta ou produto é considerado uma boa oportunidade.

Apenas mostrar preço, avaliação, vendas e comissão não era suficiente para transmitir inteligência ao usuário.

### Decisão

Foi criada uma camada local de recomendação no arquivo:

```text
src/lib/garimpa/recommendations.ts
```

Essa camada é responsável por gerar diagnósticos e sinais de oportunidade a partir dos dados já existentes no protótipo.

### A camada gera

* potencial de divulgação;
* potencial visual;
* risco de divulgação;
* canais recomendados;
* abordagem sugerida;
* motivos da recomendação;
* tags inteligentes.

### Motivo

Separar a lógica de recomendação em um arquivo próprio evita duplicação entre telas e facilita a evolução futura do produto.

A mesma lógica pode ser reaproveitada em:

* Dashboard;
* Tela de produto;
* Tela de comparativo;
* Gerador de anúncios.

### Critérios utilizados

A primeira versão considera dados como:

* preço;
* avaliação;
* número de avaliações;
* vendas aproximadas;
* comissão estimada;
* disponibilidade;
* categoria;
* ponto forte;
* ponto de atenção;
* melhor oferta calculada.

### Impacto

Com essa decisão, o Garimpa AI deixa de ser apenas um catálogo visual e passa a atuar como um assistente inicial de decisão para afiliados.

A interface passou a mostrar:

* diagnóstico no comparativo;
* diagnóstico compacto na página de produto;
* tags inteligentes nos cards;
* formatos recomendados no gerador.

### Limitações

A recomendação ainda é baseada em regras locais e dados mockados.

Ela não utiliza APIs externas, IA generativa, histórico real de preços ou dados reais de conversão.

### Status

Decisão aplicada na primeira versão da Fase 2.

## 009 — Preparar modelagem para dados reais de marketplace

**Data:** 2026-06-22

### Contexto

Após a implementação da inteligência local de recomendação, o Garimpa AI passou a precisar de uma base de dados mais próxima do que será necessário em futuras integrações com marketplaces.

A estrutura anterior de `Product` e `Offer` era suficiente para o protótipo visual, mas ainda limitada para lidar com dados reais, como identificadores externos, histórico de preço, vendedor, parcelamento, fonte dos dados e status de atualização.

### Decisão

Foi decidido expandir a modelagem interna do projeto para suportar dados mais ricos de marketplaces, mantendo compatibilidade com o MVP atual.

Os campos novos foram adicionados como opcionais para evitar quebra nos dados mockados, telas existentes e fluxos já validados.

### Alterações principais

Foram adicionados tipos auxiliares para:

* origem dos dados;
* status de sincronização;
* condição do produto;
* moeda;
* atributos técnicos;
* galeria de imagens;
* histórico de preço;
* qualidade dos dados.

Também foram adicionados campos opcionais em `Product` e `Offer` para preparar o projeto para integrações futuras.

### Motivo

A preparação antecipada da modelagem reduz o risco de retrabalho quando o projeto começar a consumir APIs reais.

Com essa decisão, futuras integrações poderão seguir o fluxo:

```text
Dado externo/API
↓
Normalizer/Adapter
↓
Product / Offer interno
↓
Dashboard, Produto, Comparativo e Gerador
```

### Impacto

A aplicação passou a suportar internamente dados como:

* marca;
* modelo;
* descrição longa;
* atributos técnicos;
* identificadores externos;
* vendedor;
* loja;
* preço anterior;
* parcelamento;
* entrega estimada;
* estoque;
* condição;
* histórico de preço;
* fonte;
* status de sincronização;
* confiança do dado.

Na interface, a primeira aplicação visual desses novos campos foi feita na tela de comparativo, exibindo metadados da oferta por marketplace.

### Limitações

A preparação ainda não consome APIs reais.

Os dados continuam sendo mockados ou locais.

Não foram adicionados scraping, autenticação, Supabase, OpenAI ou integrações externas nesta etapa.

### Status

Decisão aplicada na Fase 2.2.
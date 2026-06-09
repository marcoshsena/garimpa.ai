## 005 — Corrigir store local antes de evoluir o protótipo

**Data:** 2026-06-08

**Decisão:**  
Foi corrigido o uso de estado local no protótipo Lovable, removendo o uso problemático de `useSyncExternalStore` com dados vindos de `localStorage`.

**Motivo:**  
As páginas Produtos e Salvos apresentavam erro de carregamento causado por loop infinito de renderização. O erro acontecia porque snapshots retornavam novos arrays a cada leitura, fazendo o React entender que o estado mudava continuamente.

**Impacto:**  
O protótipo passou a ter uma base mais estável para validação local. A correção foi feita no repositório técnico `garimpa-ai-hub` e será considerada em uma futura migração para o repositório principal `garimpa.ai`.
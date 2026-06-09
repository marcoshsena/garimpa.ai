# Changelog

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
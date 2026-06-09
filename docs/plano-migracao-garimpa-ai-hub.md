# Plano de Migração — garimpa-ai-hub para garimpa.ai

## Contexto

O protótipo inicial do Garimpa AI foi criado com Lovable e sincronizado no repositório técnico `garimpa-ai-hub`.

O repositório principal do projeto será `garimpa.ai`.

## Objetivo

Definir uma estratégia segura para migrar ou reaproveitar o código do protótipo Lovable no repositório principal.

## Opções avaliadas

### Opção 1 — Migrar código completo

Copiar todo o código do `garimpa-ai-hub` para o `garimpa.ai`.

**Vantagens:**

- Mais rápido.
- Aproveita tudo que já foi gerado.
- Mantém o protótipo funcional.

**Riscos:**

- Pode trazer código gerado pouco organizado.
- Pode trazer dependências desnecessárias.
- Pode dificultar clean code se não houver revisão.

### Opção 2 — Recriar versão limpa

Usar o protótipo como referência visual e implementar uma nova base no `garimpa.ai`.

**Vantagens:**

- Código mais limpo.
- Melhor organização.
- Mais controle arquitetural.

**Riscos:**

- Demora mais.
- Exige mais implementação manual.

### Opção 3 — Migração parcial

Reaproveitar componentes, estilos e dados mockados do `garimpa-ai-hub`, mas reorganizar a estrutura no `garimpa.ai`.

**Vantagens:**

- Equilibra velocidade e qualidade.
- Permite limpar o que foi gerado.
- Mantém aprendizado do protótipo.

**Riscos:**

- Exige revisão cuidadosa.
- Pode precisar refatorar componentes.

## Estratégia recomendada

A estratégia recomendada inicialmente é a **Opção 3 — Migração parcial**.

O protótipo Lovable será usado como base visual e funcional, mas os componentes deverão ser revisados antes de entrarem no repositório principal.

## Critérios para migrar código

Antes de migrar qualquer componente, verificar:

- responsabilidade clara;
- ausência de lógica duplicada;
- nomes compreensíveis;
- ausência de chaves expostas;
- ausência de dependências desnecessárias;
- compatibilidade com futura integração Supabase;
- ausência de scraping ou chamadas externas não autorizadas.

## Próximos passos

1. Rodar o protótipo localmente.
2. Validar todas as telas.
3. Tirar screenshots.
4. Mapear estrutura de pastas.
5. Identificar componentes reaproveitáveis.
6. Definir arquitetura do `garimpa.ai`.
7. Migrar parcialmente componentes aprovados.
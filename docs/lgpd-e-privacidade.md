# LGPD e Privacidade — Garimpa AI

## Objetivo

Este documento registra cuidados iniciais de privacidade e proteção de dados para o Garimpa AI.

O projeto deve seguir uma abordagem de privacidade desde a concepção, coletando o mínimo de dados possível e deixando claro ao usuário como seus dados serão usados.

## Dados pessoais previstos na V1

A V1 poderá tratar:

- nome;
- e-mail;
- produtos salvos;
- anúncios gerados;
- histórico de uso;
- data de criação da conta;
- data do último acesso.

## Dados que não serão coletados na V1

A V1 não deve coletar:

- CPF;
- endereço;
- dados bancários;
- dados de saúde;
- dados biométricos;
- dados sensíveis;
- senhas de contas de marketplace;
- tokens de afiliado, salvo se houver implementação segura futura.

## Finalidade do tratamento

Os dados serão usados para:

- permitir acesso ao app;
- salvar produtos favoritos;
- salvar histórico de anúncios gerados;
- melhorar a experiência do usuário;
- permitir funcionamento de recursos futuros de personalização.

## Princípios adotados

O projeto adotará:

- minimização de dados;
- transparência;
- segurança;
- finalidade clara;
- revisão humana;
- exclusão mediante solicitação;
- uso de variáveis de ambiente para credenciais;
- não exposição de chaves no front-end.

## Avisos ao usuário

O app deve informar que:

- os anúncios gerados por IA devem ser revisados antes da publicação;
- o app não promete lucro;
- o app não garante comissão;
- preço e disponibilidade podem mudar;
- links de afiliado são responsabilidade do usuário.

## Segurança

Medidas previstas:

- autenticação segura;
- Row Level Security no Supabase;
- controle de acesso por perfil;
- logs sem dados sensíveis;
- variáveis de ambiente para chaves de API;
- revisão antes de integrar APIs externas.

## Solicitação de exclusão ou correção

O usuário deve ter um canal para solicitar:

- correção de dados;
- exclusão de conta;
- exclusão de histórico, quando aplicável.

## Observação

Este documento não substitui consultoria jurídica. Ele serve como guia inicial de boas práticas para o MVP.
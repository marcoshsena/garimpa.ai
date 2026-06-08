# Modelagem de Dados — Garimpa AI

## Visão geral

A V1 do Garimpa AI deve armazenar produtos, ofertas por marketplace, anúncios gerados, produtos salvos e perfis de usuários.

A estrutura abaixo é uma proposta inicial para futura implementação no Supabase.

---

## Tabela: profiles

Armazena dados básicos do usuário.

Campos:

- id: uuid, chave primária
- name: text
- email: text
- role: text
- created_at: timestamp
- updated_at: timestamp

Valores possíveis para role:

- user
- admin

---

## Tabela: categories

Armazena categorias de produtos.

Campos:

- id: uuid, chave primária
- name: text
- slug: text
- description: text
- created_at: timestamp
- updated_at: timestamp

Categorias iniciais:

- Casa e Organização
- Bebê e Família
- Tecnologia
- Games
- Beleza e Cuidados
- Ferramentas
- Cozinha
- Achados até R$ 50

---

## Tabela: products

Armazena produtos-base.

Campos:

- id: uuid, chave primária
- category_id: uuid, chave estrangeira
- name: text
- slug: text
- short_description: text
- image_url: text
- target_audience: text
- problem_solved: text
- strong_point: text
- attention_point: text
- opportunity_score: numeric
- status: text
- is_featured: boolean
- created_at: timestamp
- updated_at: timestamp

Valores possíveis para status:

- active
- draft
- paused

---

## Tabela: marketplace_offers

Armazena ofertas vinculadas a um produto.

Campos:

- id: uuid, chave primária
- product_id: uuid, chave estrangeira
- marketplace: text
- offer_title: text
- price: numeric
- rating: numeric
- social_proof: text
- shipping_info: text
- original_link: text
- affiliate_link: text
- estimated_commission_level: text
- commission_note: text
- offer_score: numeric
- is_best_option: boolean
- last_checked_at: timestamp
- created_at: timestamp
- updated_at: timestamp

Valores possíveis para marketplace:

- amazon
- mercado_livre
- shopee
- magalu

Valores possíveis para estimated_commission_level:

- high
- medium
- low
- unknown

---

## Tabela: generated_ads

Armazena anúncios gerados.

Campos:

- id: uuid, chave primária
- user_id: uuid, chave estrangeira
- product_id: uuid, chave estrangeira
- offer_id: uuid, chave estrangeira
- format: text
- content: text
- created_at: timestamp

Valores possíveis para format:

- whatsapp_short
- whatsapp_full
- instagram
- reels
- stories
- telegram

---

## Tabela: saved_products

Armazena produtos salvos por usuário.

Campos:

- id: uuid, chave primária
- user_id: uuid, chave estrangeira
- product_id: uuid, chave estrangeira
- offer_id: uuid, chave estrangeira opcional
- created_at: timestamp

---

## Regras iniciais de acesso

Usuários comuns devem poder:

- visualizar produtos ativos;
- visualizar ofertas ativas;
- salvar produtos para si;
- visualizar seus próprios produtos salvos;
- visualizar seus próprios anúncios gerados.

Administradores devem poder:

- criar produtos;
- editar produtos;
- pausar produtos;
- criar ofertas;
- editar ofertas;
- marcar melhor opção;
- atualizar dados de ofertas.

---

## Observações

A modelagem poderá mudar após testes do protótipo e integração real com Supabase.
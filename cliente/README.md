# ⚡ ZapFlow - Plataforma de Delivery via WhatsApp

O **ZapFlow** é uma solução SaaS (Software as a Service) leve e eficiente para pequenos estabelecimentos (depósitos de gás, água, rotisserias, etc.) criarem seus cardápios digitais e receberem pedidos diretamente no WhatsApp.

## 🚀 Funcionalidades Principais

* **Multi-Tenancy:** Uma única instalação serve múltiplos clientes (lojas), separados por link (ex: `/gas-fiel`, `/pizzaria-top`).
* **Painel Administrativo:** O dono da loja gerencia produtos, preços, fotos e categorias sem precisar de código.
* **Cardápio Dinâmico:** Atualização em tempo real via banco de dados.
* **Carrinho Inteligente:** Cálculo automático de totais, taxa de entrega e troco.
* **Integração WhatsApp:** O pedido final é formatado e enviado pronto para o WhatsApp da loja.
* **Gestão de Horário:** O site avisa automaticamente se a loja está "Aberta" ou "Fechada".

## 🛠️ Tecnologias Utilizadas

* **Frontend:** HTML5, Tailwind CSS (via CDN para leveza), Vanilla JavaScript.
* **Backend / BaaS:** Supabase (PostgreSQL, Auth, Storage e Realtime).
* **Hospedagem:** Vercel (Frontend) e GitHub (Versionamento).

## ⚙️ Configuração e Instalação

### Pré-requisitos
* Conta no [Supabase](https://supabase.com).
* Conta na [Vercel](https://vercel.com).

### 1. Configuração do Banco de Dados (Supabase)
No **SQL Editor** do Supabase, execute o script de criação das tabelas:

```sql
-- Criação das Tabelas Essenciais
create table public.estabelecimentos (
  id uuid default uuid_generate_v4() primary key,
  dono_id uuid references auth.users not null,
  slug text unique not null, -- Link da loja
  nome_fantasia text not null,
  telefone_whatsapp text,
  cor_primaria text default '#F97316',
  logo_url text,
  horario_abertura text default '08:00',
  horario_fechamento text default '18:00',
  valor_entrega numeric(10,2) default 0.00,
  chave_pix text
);

create table public.categorias (
  id uuid default uuid_generate_v4() primary key,
  estabelecimento_id uuid references public.estabelecimentos(id) on delete cascade,
  nome text not null,
  ordem integer default 0
);

create table public.produtos (
  id uuid default uuid_generate_v4() primary key,
  estabelecimento_id uuid references public.estabelecimentos(id) on delete cascade,
  categoria_id uuid references public.categorias(id) on delete set null,
  nome text not null,
  descricao text,
  preco numeric(10,2) not null,
  imagem_url text,
  ativo boolean default true
);

Lembre-se de ativar o RLS (Row Level Security) e criar o Bucket lojas no Storage com permissão pública.

2. Configuração do Projeto
Clone este repositório.

No arquivo admin.html e index.html, substitua as variáveis SUPABASE_URL e SUPABASE_KEY pelas suas chaves de API.

Para criar uma nova loja, acesse /admin.html e faça login com seu usuário Supabase.

📂 Estrutura de Pastas
/admin.html: Painel único de controle para todos os lojistas.

/index.html: Modelo base do cardápio (deve ser copiado para a pasta do cliente).

/cliente/NOME-DA-LOJA/: Pasta contendo o index.html específico daquele cliente (onde se define o const LOJA_SLUG).

📞 Suporte
Desenvolvido por André Freitas. Para dúvidas ou customizações, entre em contato.

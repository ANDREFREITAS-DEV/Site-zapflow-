# ⚡ ZapFlow Tecnologia - Plataforma de Vendas & Clientes

Este repositório contém o site institucional da ZapFlow (SaaS de Delivery) e a infraestrutura para hospedar os cardápios digitais dos clientes.

## 🔗 Links Oficiais
- **Site Principal:** [www.usezapflow.com.br](https://www.usezapflow.com.br)
- **Instagram:** [@usezapflow](https://instagram.com/usezapflow)
- **Contato:** comercial@usezapflow.com.br


# ZapFlow - Delivery via WhatsApp

Sistema de Cardápio Digital e Gestão de Pedidos focado em velocidade e simplicidade.
Desenvolvido com tecnologia web padrão (HTML5, TailwindCSS, JS Vanilla) e Supabase (BaaS).

## 🚀 Tecnologias
- **Frontend:** HTML5, JavaScript (ES6+), TailwindCSS (CDN).
- **Backend/Banco:** Supabase (PostgreSQL).
- **Hospedagem:** Vercel (Arquivos Estáticos).
- **Bibliotecas:** Toastify (Notificações), FontAwesome (Ícones).

## 📂 Estrutura de Pastas
O projeto utiliza uma arquitetura multi-tenant baseada em pastas:

/ (Raiz)
├── admin.html           # Painel Administrativo (Gestão de Pedidos/Cardápio)
├── cliente/             # Pasta que contém as lojas dos clientes
│   └── gas-fiel/        # Exemplo de Cliente (Slug: gas-fiel)
│       ├── index.html   # Cardápio do Cliente
│       └── pedido/      
│           └── index.html # Tela de Acompanhamento do Pedido (Recibo)
└── README.md            # Documentação

## ⚙️ Configuração
Para criar um novo cliente:
1. Duplique a pasta `cliente/gas-fiel`.
2. Renomeie para o slug do novo cliente (ex: `pizzaria-top`).
3. No `index.html` da nova pasta, altere a constante `LOJA_SLUG` no topo do script.

## 🛠️ Funcionalidades
- **Cardápio:** Listagem dinâmica por categorias.
- **Carrinho:** Controle de quantidade e subtotal em tempo real.
- **Checkout:** Envio do pedido formatado para o WhatsApp da loja.
- **Admin:**
  - Recebimento de pedidos em tempo real (Polling).
  - Impressão térmica (Cupom 58mm/80mm).
  - Gestão de status (Pendente -> Preparando -> Entrega -> Concluído).
  - Gestão de Produtos e Categorias.
  - Upload de imagens com trava de 2MB.
  - Histórico de pedidos com filtro por data.

## 📦 Banco de Dados (Supabase)
O sistema depende das tabelas: `estabelecimentos`, `categorias`, `produtos`, `pedidos`.
(Ver documentação SQL para schema completo).


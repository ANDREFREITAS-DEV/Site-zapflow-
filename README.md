# ⚡ ZapFlow Tecnologia - Plataforma de Vendas & Clientes

Este repositório contém o site institucional da ZapFlow (SaaS de Delivery) e a infraestrutura para hospedar os cardápios digitais dos clientes.

## 🔗 Links Oficiais
- **Site Principal:** [www.usezapflow.com.br](https://www.usezapflow.com.br)
- **Instagram:** [@usezapflow](https://instagram.com/usezapflow)
- **Contato:** comercial@usezapflow.com.br

# ⚡ ZapFlow - Sistema de Delivery Leve

Sistema de Cardápio Digital e Gestão de Pedidos focado em performance.
Desenvolvido para rodar direto no navegador, sem backend pesado, utilizando Supabase como banco de dados.

## 🚀 Diferenciais Técnicos
- **Arquitetura Static-First:** O site é puramente HTML/JS, garantindo carregamento instantâneo.
- **Impressão Térmica Nativa:** Gera cupons fiscais (58mm/80mm) via CSS `@media print`, compatível com impressoras USB e Bluetooth (via RawBT).
- **Multi-Tenant por Pastas:** Cada cliente tem sua própria pasta e slug (ex: `/cliente/pizzaria-x`), facilitando a gestão de URLs.

## 📂 Estrutura do Projeto
/ (Raiz)
├── index.html           # Landing Page (Venda do Serviço)
├── admin.html           # Painel do Dono (Pedidos, Cardápio, Impressão)
├── cliente/             # Diretório de Lojas
│   └── gas-fiel/        # [TEMPLATE] Pasta da Loja
│       ├── index.html   # Cardápio (Frente de Loja)
│       └── pedido/      
│           └── index.html # Tela de Acompanhamento (Recibo/Status)
└── README.md            # Documentação

## ⚙️ Como Criar uma Nova Loja
1. Copie a pasta `cliente/gas-fiel`.
2. Renomeie para o nome do novo cliente (ex: `hamburgueria-top`).
3. Edite o `index.html` da nova pasta e altere a const `LOJA_SLUG` para o slug da loja criado no banco de dados.

## 🛠️ Stack Tecnológica
- **Front:** HTML5, TailwindCSS (CDN), Vanilla JS.
- **BaaS:** Supabase (PostgreSQL, Auth, Storage, Realtime).
- **Hospedagem:** Vercel (Recomendado) ou qualquer servidor estático.

## ✅ Checklist de Funcionalidades
- [x] Cardápio Digital com carrinho e variações.
- [x] Envio de Pedido via WhatsApp (Formatado).
- [x] Painel Administrativo com atualização em tempo real (Polling).
- [x] Gestão de Status (Pendente -> Entregue).
- [x] Impressão de Comanda (Cozinha/Balcão).
- [x] Histórico de Pedidos com Filtro de Data.
- [x] Trava de segurança para upload de imagens (>2MB).
   

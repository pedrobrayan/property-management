# 🏠 Property Management

Sistema completo de gestão de imóveis para aluguel — desenvolvido para uso próprio no gerenciamento de imóveis, inquilinos, contratos e finanças.

## Sobre o projeto

Um sistema web completo para quem administra imóveis de aluguel, cobrindo desde o cadastro de propriedades até cobrança via PIX, controle de despesas mês a mês, gestão de obras/reformas e relatórios financeiros — incluindo um resumo anual de apoio à declaração de Imposto de Renda.

## ✨ Funcionalidades

- **Imóveis, inquilinos e contratos** — cadastro completo, com anexo de PDF do contrato e controle de garantia/caução (incluindo fiador e devolução)
- **Contas e despesas por mês** — cada conta fica no mês em que foi criada, com opção de repetição automática e atalho para copiar as contas do mês anterior
- **Cobrança via PIX** — geração de QR Code e código copia-e-cola (payload PIX com checksum CRC16-CCITT)
- **Central de avisos** — notificações de vencimentos (véspera, no dia e em atraso), com preferências configuráveis por tipo
- **E-mail automático diário** — resumo de pendências enviado toda manhã
- **Gestão de obras e reformas** — por imóvel, com tipo, responsável, valor e status
- **Relatórios financeiros** — gráfico de fluxo de caixa (entradas x saídas), histórico de pagamentos por inquilino e resumo anual para IR
- **Atalhos para portais oficiais** — consulta de IPTU e taxa de incêndio (RJ)
- **Multiusuário na nuvem** — login por e-mail/senha, com dados isolados por conta

## 🛠️ Tecnologias

- **Frontend:** HTML, CSS e JavaScript puro (vanilla) — sem frameworks, sem build, um único arquivo
- **Backend/Banco de dados:** [Supabase](https://supabase.com) — Postgres com Row Level Security (RLS) para isolamento de dados por usuário, autenticação por e-mail/senha e Edge Functions (Deno/TypeScript) agendadas via `pg_cron`
- **E-mail transacional:** [Resend](https://resend.com)
- **Hospedagem:** [Vercel](https://vercel.com)

## 📁 Sobre este repositório

Este repositório contém **apenas o `index.html`**, que é o frontend completo da aplicação (interface + lógica do app). 

Toda a parte de backend — banco de dados, autenticação, regras de segurança (RLS), Edge Functions e o agendamento do envio diário de e-mails — está hospedada e configurada diretamente no **Supabase**, fora deste repositório, por dois motivos:

1. Envolve credenciais e segredos (chaves de API, senhas) que nunca devem estar em um repositório de código;
2. É configuração de infraestrutura, não código-fonte versionável da mesma forma que o frontend.

O deploy do `index.html` é feito diretamente na **Vercel**, que serve o arquivo como um site estático — não há processo de build.

## 🚀 Rodando localmente

Como é um único arquivo estático, basta abrir o `index.html` em qualquer navegador. Para usar as funcionalidades de nuvem (login, sincronização, cobrança automática), é necessário um projeto próprio no Supabase configurado com a mesma estrutura de tabelas e políticas de segurança.

## 📄 Licença

Este é um projeto pessoal, desenvolvido para gestão própria de imóveis.

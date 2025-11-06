# TextHumanizer Brasil - Projeto Final (com Return URL e 30 dias Premium)

Este projeto inclui frontend e backend prontos para testar a integração com Kiwify.
Principais recursos:
- Tela de login (com dono secreto admin@gmail.com / joao151025)
- Limite gratuito de 3 minutos para usuários comuns
- Botão que abre o checkout Kiwify
- Backend com:
  - POST /api/webhook-kiwify    -> webhook do Kiwify (marca premium por 30 dias)
  - GET  /api/retorno-kiwify    -> return URL (usuário volta do checkout, ativa premium por 30 dias)
  - GET  /api/verificar-pagamento?email=...  -> verifica se e-mail está premium e retorna expiresAt
  - GET  /api/status            -> status simples do servidor

## Como testar localmente
1. Rode o backend
   ```bash
   cd backend
   npm install express body-parser cors
   node server.js
   ```
2. Rode o frontend (por exemplo, com Create React App)
   - Configure o frontend para chamar `http://localhost:3001` nas requisições de verificação.
3. No painel da Kiwify, configure o Return URL para:
   `http://SEU_BACKEND/api/retorno-kiwify`
   e o Webhook para `http://SEU_BACKEND/api/webhook-kiwify`

Observação: atualmente o backend guarda dados em memória — em produção troque por um banco de dados persistente (MongoDB, PostgreSQL, etc.).


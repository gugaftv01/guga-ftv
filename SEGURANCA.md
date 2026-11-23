# Segurança do site GUGA01FTV

## Área do organizador (modo admin)
- Na primeira tela, toque na aba **🔒 ADMIN** da barra do topo (ou 3 vezes na bola, ou no link terminando em **#admin**) e entre com **e-mail e senha** do Firebase. Sem a senha, ninguém passa da tela de entrada.
- Depois de entrar, a **Administração** aparece parada na primeira tela (só para o organizador) e, dentro de cada campeonato, acima da tabela. Nada fica flutuando.
  Não existe mais senha escrita no código.
- Organizador: a conta de acesso do futvôlei, identificada nas regras pelo código da conta (UID), sem o e-mail aparecer no código.
- **Esqueci a senha / primeiro acesso:** digite o e-mail e toque no link. O Firebase manda um e-mail para criar a senha.
- O organizador continua logado naquele aparelho até tocar em **Sair**.
- **🔒 Segurança:** mostra as últimas entradas do organizador e cada senha errada digitada (data, e-mail e aparelho).
- **Saída automática:** depois de 12 horas sem usar o modo organizador, o site pede o login de novo.
- **Senha forte:** o Firebase exige no mínimo 8 caracteres, com letra minúscula e número.
- **Privacidade do login:** as mensagens não revelam se um e-mail tem conta ou não.

## Banco de dados (Realtime Database, projeto `guga-ftv`)
Regras no arquivo `database.rules.json`:
- `chaveamento`: **todo mundo vê**; **só o organizador logado grava**.
- `bola/position`: aberto como antes (usado por outro site), mas só aceita números `x` e `y`.
- `tentativas`: o site só acrescenta registros (com a hora do servidor); só o organizador lê e apaga.
- `acessos`: registro de cada entrada do organizador; só ele grava e lê.
- Qualquer outro caminho: fechado.

As regras antigas eram de "modo de teste": **qualquer pessoa podia apagar ou trocar os resultados**, e elas
**venceriam em 22/12/2026**, quando o site pararia de funcionar. Isso foi corrigido.

Para ter outro organizador: crie o usuário em **Authentication → Usuários**, copie o **UID** dele e troque a condição
nas regras por `auth.uid === 'UID1' || auth.uid === 'UID2'`. Publique em **Realtime Database → Regras**.

## Chave do Firebase
A chave só funciona a partir dos endereços do GitHub Pages do site e dos endereços
do próprio Firebase, e só para os serviços usados (Google Cloud → APIs e serviços → Credenciais).
**Se o site for colocado em outro endereço (ex.: Google Sites ou domínio próprio), adicione esse endereço na chave.**

## Backup
Antes das mudanças foi feito um backup completo do banco. Para baixar outro: **Realtime Database → Dados → ⋮ → Exportar JSON**.

## Proteções do site (OWASP Top 10 2025)
- **Regra de segurança (CSP):** o site só carrega código e se conecta aos endereços do Firebase.
- **Impressão digital (SRI):** as bibliotecas do Firebase só rodam se forem exatamente as originais.
- **Sem cópias antigas publicadas:** a pasta `files/` (cópia antiga com a senha velha) foi removida.

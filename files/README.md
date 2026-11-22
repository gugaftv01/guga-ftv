# GUGA01FTV – Chaveamento de Futvôlei

Site do torneio de futvôlei (dupla eliminação), com resultados salvos no Firebase.

## Arquivos
- `index.html` – o site inteiro (é este que o GitHub Pages abre)
- `.nojekyll` – avisa o GitHub para publicar o site do jeito que está
- `README.md` – este guia

## Como colocar no ar (GitHub Pages)
1. Entre em https://github.com e crie uma conta com o nome de usuário **gugaftv01**
   (assim o endereço fica `https://gugaftv01.github.io`).
2. Clique em **New repository** e dê o nome **gugaftv01.github.io** (deixe como *Public*).
3. Na página do repositório, clique em **uploading an existing file** e arraste os arquivos
   `index.html`, `.nojekyll` e `README.md`. Clique em **Commit changes**.
4. Vá em **Settings > Pages**. Em *Branch*, escolha **main** e **/ (root)**, e clique em **Save**.
5. Espere 1 a 2 minutos e abra `https://gugaftv01.github.io`.

## Para mudar o site depois
Abra o `index.html` no repositório, clique no lápis (Edit), faça a alteração e clique em **Commit changes**.
Ou envie o arquivo novo pelo mesmo caminho do passo 3 (substitui o antigo).

## Banco de dados
Os resultados ficam no Firebase (Realtime Database, projeto `guga-ftv`, caminho `chaveamento`).
Confira em **Realtime Database > Regras** se a leitura e a gravação de `chaveamento` estão liberadas.

## Domínio próprio (opcional)
Se um dia comprar um domínio (ex.: gugaftv01.com.br), crie um arquivo chamado `CNAME` nesta pasta
com só o domínio escrito dentro e aponte o DNS para o GitHub Pages.

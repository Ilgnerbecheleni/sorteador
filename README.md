# Amigo Oculto — sorteador online

Site estático responsivo para organizar amigo oculto com 2 ou mais participantes, sem limite fixo. Funciona no GitHub Pages, sem backend ou banco de dados.

## Como usar

1. Cadastre os nomes (mínimo de 2) e adicione quantas pessoas quiser.
2. Clique em **Fazer sorteio**. Ninguém tira o próprio nome e cada pessoa é sorteada uma vez.
3. Copie o link individual ou envie diretamente pelo WhatsApp.
4. Cada participante abre seu link e clica em **Revelar meu amigo oculto**. Não há códigos ou confirmação obrigatória.
5. O sorteio vigente fica salvo no navegador. Mesmo após fechar ou recarregar a página, a lista e os links permanecem iguais.
6. Quando desejar, o organizador clica em **Encerrar sorteio** e confirma. O sorteio ativo é removido, mantendo os nomes para facilitar um novo sorteio.

## Persistência e privacidade

- Os nomes e os links do sorteio ativo são salvos no LocalStorage do navegador do organizador.
- Use o mesmo dispositivo, navegador, perfil e endereço do site. Limpar os dados do site, usar navegação anônima ou trocar de aparelho pode causar perda dos dados.
- Sorteios salvos na versão anterior são preservados; links das versões 1, 2 e 3 continuam abrindo normalmente.
- Cada convite contém apenas o resultado individual, protegido com AES-GCM. A chave está no próprio link: qualquer pessoa que tenha acesso a ele pode revelar o resultado.
- Encerrar um sorteio remove a lista local, mas **não revoga os links já enviados**. Os convites são autocontidos e continuam funcionando sem um servidor.
- Não compartilhe os links em grupos. Os dados de participantes não são enviados ao repositório.

## Publicar no GitHub Pages

O workflow em `.github/workflows/deploy-pages.yml` publica a branch main.

1. No repositório, abra **Settings → Pages**.
2. Em **Build and deployment**, selecione **GitHub Actions**.
3. Em **Actions**, execute **Publicar Sorteador (GitHub Pages)** se necessário.

Endereço previsto: https://ilgnerbecheleni.github.io/sorteador/

## Arquitetura

- HTML, CSS e JavaScript em `index.html`
- LocalStorage para persistência local
- Web Crypto API (AES-GCM e aleatoriedade criptográfica)
- HTTPS para utilização da Web Crypto API
- GitHub Actions para deploy estático

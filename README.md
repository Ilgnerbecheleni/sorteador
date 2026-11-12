# Amigo Oculto — sorteador online

Site estático responsivo para organizar um amigo oculto com 2 ou mais participantes, sem limite fixo de pessoas. Funciona no GitHub Pages, sem backend, Node.js ou banco de dados.

## Como usar

1. Cadastre os nomes (no mínimo 2). Adicione ou remova participantes.
2. Clique em **Fazer sorteio**. O site cria um ciclo aleatório: ninguém tira o próprio nome e cada pessoa é sorteada uma vez.
3. Libere o link individual de cada participante e copie ou envie pelo WhatsApp.
4. O participante abre seu convite, aceita e revela o resultado. Seu aceite gera um código individual (AC-...).
5. Ele envia o código ao organizador pelo WhatsApp ou outro meio. No painel, cole o código em **Registrar aceite do participante**.
6. O painel registra o aceite e atualiza o progresso. O próximo sorteio só é permitido após todos os links serem liberados e todos os aceites serem registrados.

## Persistência e privacidade

- Os nomes, sorteio ativo, links, estados de liberação e aceites ficam no LocalStorage do navegador do organizador.
- O sorteio não é apagado automaticamente ao recarregar, fechar ou concluir a página. Após a conclusão, o organizador pode escolher iniciar outro sorteio.
- Se o participante aceitar em outra aba do mesmo navegador e perfil do organizador, o aceite é registrado automaticamente quando possível. Em outro dispositivo, o código precisa ser enviado e registrado manualmente.
- O aceite do participante também é salvo no navegador dele. O link continua válido após recarregar.
- LocalStorage não é um banco de dados compartilhado: apagar os dados do site, trocar de dispositivo ou perfil, ou usar navegação anônima pode causar perda de dados. Use o mesmo navegador e endereço do site.
- Links v1, gerados antes desta atualização, ainda podem revelar o resultado, mas não possuem código de confirmação e não são recuperáveis se o sorteio antigo já foi perdido.
- Cada convite contém somente o resultado individual e seu código, protegido com AES-GCM. A chave está no próprio link: qualquer pessoa que tenha acesso ao link pode revelar o resultado. Não compartilhe os links em grupos.
- Liberação e aceite são controles locais de fluxo, não autenticação ou prova de identidade. Um organizador com acesso técnico aos links pode inspecioná-los.

## Publicar no GitHub Pages

O workflow em `.github/workflows/deploy-pages.yml` publica automaticamente a branch main.

1. No repositório, abra **Settings → Pages**.
2. Em **Build and deployment**, selecione **GitHub Actions**.
3. Em **Actions**, execute **Publicar Sorteador (GitHub Pages)** se necessário.
4. Acompanhe a execução até a publicação.

Endereço previsto: https://ilgnerbecheleni.github.io/sorteador/

O plano GitHub Free exige repositório público para GitHub Pages. Um repositório privado pode exigir um plano compatível. O sorteio e os convites não são gravados no repositório.

## Arquitetura

- HTML, CSS e JavaScript nativos em `index.html`
- LocalStorage para persistência do organizador e do participante
- Web Crypto API (AES-GCM, números aleatórios seguros)
- HTTPS necessário para o funcionamento da Web Crypto API
- GitHub Actions para deploy estático

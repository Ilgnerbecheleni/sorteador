# Amigo Oculto — sorteador para 3 pessoas

Site estático (um único `index.html`), responsivo e pronto para publicar, sem Node, backend, contas ou banco de dados.

## Funcionalidades

- Recebe exatamente 3 nomes distintos.
- Sorteio criptograficamente aleatório, em ciclo de 3: cada pessoa tira uma pessoa diferente, e todos são sorteados uma vez.
- Cria três links individuais; o organizador vê os links, mas não os resultados na tela.
- A pessoa abre seu link e clica em **Revelar meu amigo oculto**.
- Links cifrados localmente com AES-256-GCM usando Web Crypto API. O segredo para abrir o resultado está contido no próprio link.
- Botões **Copiar link**, **Enviar no WhatsApp**, **Copiar todos os links** e **Salvar em TXT**.

## Publicação mais fácil: Netlify Drop

1. Entre em https://app.netlify.com/drop
2. Envie o arquivo `index.html` ou arraste a pasta `amigo-oculto-3`.
3. Abra o endereço publicado, normalmente terminado em `.netlify.app`.
4. **Só faça o sorteio depois de publicar**, para que os links já apontem ao endereço público.
5. Cadastre os nomes, sorteie, envie cada link individualmente por WhatsApp e guarde uma cópia dos links.

## Publicação alternativa: Cloudflare Pages

1. Acesse Cloudflare > **Workers & Pages** > **Create application** > **Get started** > **Drag and drop your files**.
2. Faça upload desta pasta ou do ZIP.
3. Escolha o nome do projeto e publique.
4. Abra o domínio `.pages.dev` fornecido e faça o sorteio por lá.

## Testar localmente

Abra `index.html` com um navegador moderno. Para maior compatibilidade, prefira servir em `http://localhost` (que é considerado um contexto seguro) ou em um site HTTPS. O aplicativo precisa de **Web Crypto API**.

## Cuidados importantes

- **Os links não ficam salvos no servidor**: salve o TXT antes de fechar ou atualizar a página.
- **Qualquer pessoa com acesso a um link poderá abrir aquele resultado.** Envie cada link apenas ao destinatário certo. O link é um segredo de acesso, não um login.
- Links criados antes de mudar o endereço/domínio do site continuarão apontando para o endereço antigo. Sorteie de novo após a publicação definitiva.
- Não há botão para invalidar um link enviado: para trocar os resultados, gere um novo sorteio e avise a todos para desconsiderar os links anteriores.
- Com **exatamente 3 pessoas**, há apenas **duas distribuições possíveis** em que ninguém tira a si mesmo. Portanto, conhecendo os três nomes e apenas um par, alguém consegue deduzir os outros dois. O aplicativo protege os links de exposição casual, mas **não é possível garantir sigilo matemático dos resultados entre três participantes**.
- Se o organizador tiver acesso a todos os links, tecnicamente poderá abri-los para conhecer os resultados, embora o painel não os exiba.

## Estrutura

```
amigo-oculto-3/
├── index.html
└── README.md
```

Não há bibliotecas externas nem serviços pagos.
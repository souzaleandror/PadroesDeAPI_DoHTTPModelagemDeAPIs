#01/07/2026

Padrões de API: Do HTTP à modelagem de APIs

Faça esse curso de Computação e:
Compreenda o protocolo HTTP e sua importância para as APIs
Crie APIs utilizando mockAPI para facilitar o teste e desenvolvimento
Use o Postman para executar chamadas e testar APIs de forma eficaz
Entenda os diferentes padrões de API e como escolher o mais adequado para cada projeto
Aprenda estratégias para a modelagem de APIs, incluindo decisões sobre endpoints, métodos HTTP e estruturas de dados
Explore a comunicação em tempo real com APIs
Entenda as práticas recomendadas para a documentação de APIs

@01-Bem começado, metade feito

@@01-Apresentação

Olá, pessoal! Boas-vindas à Alura. Meu nome é Vinícius Dias e vou guiar você neste curso sobre padrões de modelagem de API.

Audiodescrição: Vinícius se autodeclara como um homem branco. Tem cabelo escuro e curto, usa bigode e cavanhaque rentes ao rosto. Está de camisa preta com uma pequena cruz de malta vermelha estampada no peito. À sua frente, um microfone apoiado num braço articulado. Ao fundo, uma parede lisa e um ambiente com iluminação arroxeada.

Para quem é este curso?

Se você já domina programação web em qualquer linguagem de programação e entende o protocolo HTTP, mas deseja entender o que é uma API e como criar esse tipo de sistema que vai ser acessado por outros sistemas, este curso é para você!

O que aprenderemos?

Neste curso, aprenderemos primeiramente o que é uma API e em que cenários uma API pode ser útil.

Para isso, vamos precisar de algumas ferramentas. Vamos instalar um cliente HTTP e criar uma API fictícia, para não precisar escrever código enquanto focamos nos conceitos. Assim, conseguiremos executar chamadas para uma API real, porque vamos criá-la de forma simples.

Em seguida, vamos entrar com bastante detalhe no HTTP, aprofundando bastante nossos conhecimento nesse assunto, inclusive lendo pedaços da RFC, a especificação formal do HTTP.

Posteriormente, vamos falar sobre padrões de APIs, abordando padrões antigos, que não são mais tão utilizados, padrões atuais e até recursos mais modernos.

Feito isso, vamos conversar bastante sobre modelagem de APIs, entendendo quais decisões precisamos tomar e como normalmente essas decisões são tomadas, e conhecendo alguns padrões comuns para modelagem de APIs.

Em seguida, vamos discutir, mesmo que de forma rápida, sobre comunicação em tempo real. Vamos entender algumas formas com que uma API pode fornecer comunicação em tempo real para o cliente e também receber informações em tempo real.

No final, teremos uma conversa rápida sobre documentação de API.

Dicas de estudo

Se ao longo das aulas algum detalhe não ficar muito claro e você tiver qualquer dúvida, não hesite em abrir tópico no fórum do curso! Com certeza alguém vai conseguir responder à sua questão, pois temos uma grande comunidade de pessoas estudantes, moderadoras e instrutoras prontas para te ajudar.

Se você quiser uma interação um pouco mais dinâmica, convidamos você a fazer parte do nosso servidor do Discord. Lá temos uma comunicação um pouco mais instantânea e você pode conversar mais aprofundadamente com pessoas da comunidade.

Mais uma vez: boas-vindas! Esperamos que você tire bastante proveito deste curso. Esperamos você no próximo vídeo para começarmos a configurar nosso ambiente e instalar o que for necessário para aprender bastante sobre APIs.

@@02-Clientes HTTP

Antes de explorarmos uma API, precisamos de uma ferramenta para utilizá-la.

Isso porque, quando acessamos algum sistema web, normalmente fazemos isso pelo navegador. No entanto, ao acessar uma URL diretamente pelo navegador, não enviamos nenhuma informação além da página que queremos acessar, sem informar diversos parâmetros que uma API, por exemplo, nos permitiria enviar - como informações adicionais, padrões alternativos e verificações que o navegador não exibe normalmente.

Vamos utilizar uma das ferramentas possíveis para isso: um cliente HTTP. Uma API é servida através de um servidor HTTP, então precisamos de um cliente HTTP poderoso para realizar essas tarefas utilizando uma API.

Poderíamos utilizar ferramentas de linha de comando, como o cURL, mas vamos optar por algo mais gráfico. Uma das opções é o famoso Postman - plataforma que introduzimos em outros conteúdos disponíveis na Alura.

O Postman permite que façamos requisições e examinemos as respostas de APIs, realizando tudo que for necessário para qualquer manipulação de API.

O Postman possui uma versão paga, mas a versão Community, gratuita, nos atende perfeitamente bem.

Para quem não gosta muito do Postman, seja pelo fato de não ser totalmente gratuito, ou por não ser de código aberto, ou até pelo próprio visual, há outra opção: o Insomnia. Essa plataforma é criada e mantida pela empresa Kong, que tem algumas outras ferramentas de código aberto. O Insomnia também tem um plano gratuito que nos atende perfeitamente bem, e algumas pessoas consideram seu visual mais moderno.

Ambas as ferramentas, Postman e Insomnia, nos servirão para realizar requisições para API.

Vale mencionar que a sua IDE, que você utiliza para programar na sua linguagem de programação ou mesmo criar sua API, muito provavelmente tem um cliente HTTP embutido também - seja criando arquivos .http ou tendo uma interface que permita fazer requisições HTTP.

Caso você não utilize uma IDE, mas um editor de código, talvez exista uma extensão que possa realizar requisições HTTP diretamente pelo seu editor de código.

Neste curso, vamos utilizar o Postman porque é a ferramenta com a qual o instrutor está mais habituado, mas você pode utilizar a que preferir sem nenhum problema - seja Postman, Insomnia, linha de comando com o cURL, sua IDE ou qualquer cliente HTTP que te permita alterar os parâmetros da requisição vai te servir bem durante este curso.

Agora que já entendemos sobre as ferramentas e sobre o cliente HTTP, vamos criar um servidor HTTP, uma API, para que possamos testar alguns recursos e entender conceitos na prática.

@@03-Para saber mais: o que é uma API

APIs (Application Programming Interfaces) são muito utilizadas no dia-a-dia de nós devs, mas o que APIs realmente são? O que é uma API, na prática?

Nesse vídeo a gente vai entender o que é API com alguns exemplos simples de entender.

@@04-Para saber mais: Postman

Neste vídeo falaremos sobre como interagir com APIs. O Postman é uma ferramenta que nos ajuda a realizar algumas verificações em APIs de forma gráfica e simplificada.

Utilizar o navegador não é suficiente para fazermos requisições POST, DELETE, PUT e etc. Utilizar o cURL ou alguma outra ferramenta da linha de comando pode ser complexo e trabalhoso. Por isso Postman é uma ótima solução para este caso.

Transcrição

Olá, Pessoal, meu nome é Vinícius Dias e hoje vamos falar um pouco sobre como fazer alguns testes com APIs.

É uma situação bastante corriqueira quando estamos desenvolvendo algum sistema e precisamos integrar com outro sistema, seja um sistema nosso ou um sistema externo. Uma das formas de integração mais comum é através de APIs.

Imagine que estamos desesnvolvendo um aplicativo para um blog e preciso consumir essa API de comentários de todos os posts, então precisamo de um API, que vocês já devem ter percebido que não foi desenvolvido por mim, mas eu vamos utilizá-lo aqui já que ele traz todos os comentários.

Se precisarmos verificar o retorno de uma API podemos colar a URL no navegador e apartir disso conseguimos visualizar a resposta. Mas temos alguns probleminhas. Primeiro, temos só o corpo. Para visualizarmos os cabeçários da aquisição teriamos que abrir a aba de redes do Chrome etc. Além disso, não temos syntax highlighter, não tmos uma das features tão legais que editores de código ideais fornecem, por isso a leitura fica um pouco prejudicada.

O principal problema, se formos utilizar navegadores para testar APIs para verificar respostas e testar requisições, é que uma requisição do tipo post ou com qualquer outro verbo http não é tão simples. Não consiguimos vir aqui e colocar a URL e selecionar o verbo http. Teríamos que, por exemplo, ir na aba de desenvolvedores no console sabendo JavaScript, teríamos que fazer um fetch() para URL informar os dados. Não é algo tão prático.

Então existem algumas opções, algumas aliternativas, uma dessas alternativas é o curl. Utilizando ele conseguimos fazer uma requisição do tipo post tranquilamente. E aqui eu consigo passar cabeçalhos, por exemplo informar que o content type dessa requisição é do tipo application/json.


Copiar
curl -X POST -H 'Content-Type: application/json'
E informar que o corpo é um json onde precisamos informar postID o nome (name), o email e o corpo (body).


Copiar
{
“postID”: 1,
“id”: 1,
“name”: “id labore ex et quam laborum”,
“email”: “Eliseo@gardner.biz”,
“body”: laudatium enim quasi est quidem magmam voluptate ipsam eos\ntempora quo necessitat\ndolor quam autem quai\nreiciendis est nam sapiente accusantium”
}
Reparem que isso pode ficar complicado. Então primeiro vamos passar o postID 1 o name é Vinicius Dias o email é vinicius@alura.com.br e o body do comentário é Meu comentário de teste. Por fim, vamos informar a URL.


Copiar
“postID”: 1,
“name”: “Vinícius Dias”,
“email”:  “vinicius@alura.com.br”,
“body”: “Meu comentário de teste”,
“id”: 501
Conseguimos através de uma ferramenta relativamente simples e bastante poderosa fazer uma requisição do tipo post. Porém, temos ainda alguns problemas, por exemplo, não temos syntax highlighter por padrão.

Para fazer esse tipo de teste, podemos utilizar o Postman. Acessando o site, na página principal, teremos o botão “Dowload” e devemos clicar nele para baixar a ferramenta.

https://jsonplaceholder.typicode.com/comments

@@05-Navegador
DISCUTIR NO FÓRUM
Ana vai trabalhar consumindo uma API disponibilizada por você, e para isso ela pretende usar o próprio navegador padrão que utiliza para as demais tarefas.

Por que Ana deveria utilizar um cliente HTTP especializado em consumo de APIs em vez de um navegador web?

Porque o navegador não permite acesso a APIs, somente a sites.


Porque o navegador sempre envia requisições GET sem corpo ao acessar uma página.

Ao digitar um endereço no navegador, uma requisição é feita ao servidor, porém nós não podemos configurá-la. Com um cliente HTTP, como Postman ou Insomnia, podemos definir o método, os cabeçalhos e o corpo da requisição, além de termos acesso mais facilitado a todos os detalhes da resposta também.


C
Porque o navegador tem muitos recursos, tornando o acesso à API mais lento.


D
Usar um navegador é uma opção perfeitamente válida e produtiva para consumir uma API.

@@06-API de exemplo

Já temos um cliente HTTP para realizar requisições e inspecionar as respostas - seja o Postman ou qualquer outra plataforma. Seguiremos usando o Postman como exemplo.

Agora, vamos criar um servidor. Poderíamos criar uma API, já que somos pessoas que escrevem código. No entanto, isso nos faria focar em outros detalhes e não tanto na teoria por trás da criação e modelagem de padrões de API. Além disso, teríamos que escolher uma linguagem de programação, com a qual você pode não ter familiaridade.

Para não precisarmos escrever código, mas ainda assim praticar alguns conceitos relacionados à API, vamos utilizar um serviço interessante: o mockapi.io. Esse serviço permite que você crie APIs fictícias, super simples, que retornam alguns dados que você pré-definir.

Criando um projeto no mockAPI

A API que esse sistema cria já é bem completa, com muitos recursos que precisaremos estudar, mas também tem alguns problemas que utilizaremos como exemplo para entender como poderíamos melhorar e discutir possíveis soluções.

Então, acesse o mockAPI e crie a sua conta com nome, e-mail e senha. O plano gratuito permite a criação de um projeto, que é tudo que precisaremos.

Vamos criar um projeto juntos. Na página inicial do mockAPI, vamos clicar no botão "New project" no topo da página (símbolo de adição). Na janela modal de criação de projeto, vamos nomeá-lo no campo "Name". Podemos chamar esse projeto de API Cursos, porque ela será uma API semelhante à Alura, que fornece cursos, apenas como exemplo.

Ela janela também pede um prefixo (campo "API Prefix"), opcional, que será adicionado a todos os endpoints desse projeto. Um endpoint é, resumidamente, uma URL que acessamos na nossa API para realizar alguma ação. Falaremos mais sobre isso adiante.

Podemos definir esse prefixo como /api, só para identificar o que é da API do nosso sistema. Pode ser que você tenha um sistema que é uma aplicação web com uma interface, e tudo que for /api é a API do seu sistema, fornecido para os clientes.

Vamos clicar em "Create" para confirmar a criação do projeto. Pronto! Ele será adicionado à página inicial de projetos da nossa conta.

Configurando schema e endpoints da API

Podemos clicar no projeto que criamos nessa lista de projetos da conta para abri-lo. Nas informações, temos a URL completa dessa nossa API, com o nosso prefixo /api, e o final /:endpoint, que será o nome de um recurso da nossa API.

No sistema mockAPI, e em um padrão de APIs muito conhecido, um recurso é um detalhe do seu domínio que vamos manipular utilizando uma API. Por exemplo, na API de cursos, vamos buscar, inserir e remover cursos, ou seja, vamos manipular cursos. Então, os cursos podem ser considerado um de nossos recursos.

Para criar um novo recurso, clicamos no botão "New resource" do projeto criado. Na janela modal de criação do recurso, vamos definir seu nome como cursos, em português, tudo minúsculo, no plural. Falaremos mais a fundo sobre esses padrões de nomeação adiante.

Em seguida, podemos definir um "Schema" (esquema) do nosso recurso, ou seja, estruturar basicamente quais informações sobre um curso teremos nessa API fictícia.

Por padrão, já temos sugeridos os itens id (identificador), createdAt (data de criação), name (nome) e avatar (imagem). Podemos mudar o createdAt para data_criacao, para deixar tudo em português. O name vai ser titulo, pois um curso vai ter um título, no lugar do avatar podemos colocar uma descricao (tudo sem acento).

Também conseguimos informar como esse valor será criado, caso queiramos criar vários dados automaticamente. No campo data_criacao teremos uma data recente (date.recent), o titulo pode ter um dado do tipo company.name, para salvar como o nome de uma empresa e não o nome de uma pessoa e diferenciar essa informação. Na descricao poderíamos ter qualquer texto, então vamos colocar o lorem.text, que significa "texto aleatório" - ou seja, uma descrição pode ser qualquer coisa.

Nosso schema com título, descrição e data da criação é suficiente. Poderíamos adicionar mais informações clicando no botão "Add field" (ícone de adição), mas não é necessário nesse momento.

Além disso, na versão paga, poderíamos criar o template desse objeto com mais informações, além desse schema mais simples, mas não vamos precisar disso neste curso.

Por fim, rolando essa janela para baixo, podemos definir os nossos endpoints. Ou seja, quando formos manipular cursos, o que podemos fazer com eles? Quais são os endpoints disponíveis?

Podemos buscar todos os cursos, buscar um único curso, inserir um novo curso, remover um curso e assim por diante? Todas essas ações são endpoints, e nesse momento informamos quais estarão disponíveis nesse projeto.

Se quiséssemos, poderíamos modificar a resposta que esse endpoint traz. Não precisamos fazer isso agora, então vamos deixar tudo ativado, como padrão, e clicar em "Create".

Nossa API foi criada! Ao clicar em "Data", conseguiríamos verificar todos os cursos adicionados. No nosso caso, ainda não temos nenhum curso registrado na nossa API.

Acessando a API

Vamos tentar acessar essa API. Quando clicamos no nome "cursos", temos acesso a uma URL em uma nova aba do navegador. E essa URL é a que vamos utilizar no Postman para criar uma nova requisição (ou seja qual for o seu servidor). Copiamos.

Para criar uma nova requisição no Postman, clicamos no botão com símbolo de adição (+) no menu de abas superior. Repare que temos palavras como GET ou POST antes do campo de URL da requisição. Vamos apenas manter o GET padrão e falar mais sobre isso em breve. Depois, colamos a URL que copiamos do mockAPI.

Quando clicamos em "Send" e enviamos essa requisição, recebemos como resposta um array vazio, na aba "Body" na parte inferior do Postman.

GET


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos

[]

Repare que o Postman nos mostra muitas informações. Além do corpo da resposta, que é um array vazio no momento, poderíamos consultar a aba "Cookies" e verificar que não tem nada sendo enviado. Também temos os cabeçalhos, na aba "Headers", e também o status da resposta, quanto tempo ela levou para ser executada e quanta memória ela ocupa. O seu cliente HTTP deverá trazer informações semelhantes a essas.

Conclusão

Com isso, temos a nossa API pronta para começarmos a discutir alguns assuntos como, por exemplo, o que é esse tal de GET, quais são essas outras opções de requisição e o que significa cada uma delas.

Mesmo que você já conheça os métodos HTTP, ainda assim, na próxima aula, vamos conhecer alguns detalhes mais profundos sobre eles.

@@07-Faça como eu fiz: crie uma API
DISCUTIR NO FÓRUM
Nesta aula, aprendemos o que é uma API e como acessar uma API utilizando um Cliente HTTP.

Agora é sua vez! Chegou a hora de você criar uma API utilizando o mockAPI.

Opinião do instrutor
•

Opções
Acesse o site do mockAPI;
Crie uma conta gratuita;
Crie um novo projeto para o curso;
No projeto recém-criado, crie um recurso;
Acesse os endpoints desse recurso usando o cliente HTTP escolhido (Postman, Insomnia, cURL, sua IDE favorita ou outro).

https://mockapi.io/

https://mockapi.io/

@@08-O que aprendemos?
DISCUTIR NO FÓRUM
Nesta aula, nós:

Aprendemos o que é uma API, qual o seu propósito e quando utilizar uma API;
Conhecemos clientes HTTP específicos para consumo de APIs, como Postman e Insomnia;
Criamos uma API de exemplo para praticarmos os conceitos que serão vistos no curso.


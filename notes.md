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

#02/07/2026

@02-HTTP

@@01-Métodos da requisição

Agora é o momento de nos aprofundarmos em alguns detalhes.

Métodos HTTP

No Postman, temos acesso a várias opções para criar requisições: GET, POST, PUT, PATCH, DELETE, ADD e OPTIONS. Esses são métodos HTTP.

Esses métodos indicam o que desejamos fazer com o recurso que estamos acessando na URL.

Por exemplo, se utilizamos o método GET para acessar o nosso endpoint de /cursos, significa que desejamos recuperar ou buscar todos os cursos disponíveis. Já se utilizamos o método POST, usaremos o corpo da requisição para enviar informações e criar um curso.

Em teoria, o método que usamos na API ditará qual ação desejamos tomar ou executar naquele recurso.

Analisando os endpoints

A origem dessa teoria pode ser entendida por partes. Primeiro, pegamos a documentação da mock API para verificarmos quais são os endpoints que ela gera.

Method	URL	Payload	Response	Description
GET	/tasks		Task[]	Get a list of tasks
GET	/tasks/{taskId}	Task	Task	Get a task by ID
POST	/tasks	Task	Task	Create a new task
PUT	/tasks/{taskId}	Task	Task	Update a task
Patch	/tasks/{taskId}	Task	Task	Update a task
Delete	/tasks/{taskId}	Task	Task	Delete a task
Temos uma url com o método GET para o nome do nosso recurso na /. O recurso usado como exemplo é tasks; no nosso caso, é cursos. Se fazemos um GET para /cursos, ele buscará a lista de cursos. Se fazemos um GET para /cursos/ seguido do id daquele curso, ele buscará apenas o curso específico.

Voltamos ao Postman.

Acessando /api/cursos/1 utilizando o método GET, obtemos um erro:


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos/1

"Something went wrong while parsing response JSON" ("Algo deu errado ao analisar o JSON de resposta")

Algo está gerando esse erro na API, mas voltaremos nisso depois. Voltamos à documentação.

Ao enviar um POST para /cursos, um novo curso é criado. Quando usamos PUT em /cursos/id, o curso é atualizado. O método PATCH também atualiza o curso, funcionando de forma semelhante ao PUT, mas com distinções que serão explicadas em breve. Finalmente, o método DELETE remove o curso.

A Mock API gera esses endpoints para nós. No entanto, a decisão sobre como cada método HTTP deve ser utilizado não foi feita arbitrariamente pela Mock API. Existe um padrão e uma recomendação para o propósito de cada um desses métodos, derivados das especificações do próprio HTTP.

RFC 7231

Acessamos a RFC 7231, que trata da semântica e do conteúdo do HTTP. Nesta aula, focaremos na definição dos métodos ("Method Definitions") do lado direito.

Temos toda a explicação do propósito de cada método e algumas de suas características, que discutiremos em breve.

Método GET

O GET solicita o recurso, pedindo a representação desse recurso específico. No caso, ao fazer um GET em /cursos, estamos requisitando os cursos.

Método HEAD

O método HEAD funciona como o GET, exceto que não retorna o corpo da resposta. Ao realizar uma requisição do tipo HEAD, esperamos receber apenas os cabeçalhos. Isso pode ser útil em cenários onde desejamos verificar o tamanho da resposta antes de decidir se iremos processá-la. Também é útil para determinar o tipo de resposta antes de recebê-la. Em breve, discutiremos mais sobre cabeçalhos.

O método GET e o HEAD são essencialmente iguais, exceto pelo fato de que o HEAD não traz o corpo da resposta.

Método POST

O método POST espera a entrega de um pedaço de informação, um payload, como corpo da requisição. Esse corpo será utilizado como representação desse recurso.

Voltamos ao Postman para tentarmos utilizar a API.

Visualizando e Enviando dados com Postman

Com o método GET, temos o seguinte endereço:


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos/1

Clicamos em "Body" abaixo do endereço, e depois em "raw" para enviar um corpo. Optamos por raw no body para enviar texto cru. Escolhemos o formato JSON do lado superior direito, usado para enviar dados.

No campo de texto, abrimos e fechamos as chaves para iniciar o JSON, {}. Selecionamos o título deste curso como "Curso de API". Para isso, inserimos "titulo": "Curso de API" entre aspas duplas e dois pontos. A descrição será "Curso sobre Padrões de API".


Copiar
{
  "titulo": "Curso de API",
  "descricao": "Curso sobre padrões de API"
}

Vamos verificar o que ocorre ao tentarmos realizar uma requisição do tipo POST para o **endpoint api/cursos **sem incluir a data de criação.


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos

Clicamos no botão "Send" ("Enviar") do lado superior direito. Analisando em "Body > Pretty" na parte inferior, temos:


Copiar
{
  "data_criacao": "2024-05-10T17:01:53.539Z",
  "titulo": "Curso de API",
  "descricao": "Curso sobre padrões de API",
  "id": "1"
}

Observe que a data de criação foi gerada automaticamente com base na configuração da API. Temos as informações do título que enviamos e da descrição que enviamos. Acabamos de criar um novo curso. Portanto, o POST funciona assim: enviamos sua representação para o servidor e ele a armazena.

Ao tentarmos buscar todos os cursos inserindo o método GET no mesmo endereço e clicando em "Send", obtemos um array de cursos.


Copiar
[

    {

        "data_criacao": "2024-05-10T17:01:53.539Z",

        "titulo": "Curso de API",

        "descricao": "Curso sobre padrões de API",

        "id": "1"

    }

]

Ao buscarmos apenas o curso com o id 1, inserindo /1 no endereço, encontramos esse curso recém inserido.


Copiar
    {
        "data_criacao": "2024-05-10T17:01:53.539Z",
        "titulo": "Curso de API",
        "descricao": "Curso sobre padrões de API",
        "id": "1"
    }

Observe que há uma diferença entre os métodos.

Agora, focaremos nos mais relevantes, aqueles que têm diferenças significativas. Voltamos à documentação.

Atualizando recursos com PUT

O método PUT requer que a representação de dados enviada no corpo da requisição substitua completamente o conteúdo existente no servidor.

Isso significa que em uma API RESTful completa (discutiremos sobre esse termo em breve), ou seja, em uma API que segue todos os padrões da especificação, o cenário é o seguinte: ao tentar realizar uma requisição PUT para api/cursos/2 com um ID que não existe e enviar um corpo na requisição, a API tentará atualizar esse curso com as informações fornecidas (título e descrição).

A API do MockAPI não suporta essa funcionalidade. Quando fazemos essa requisição clicando em "Send", temos como retorno um "Not found" ("Não encontrado"). Isso porque o método PUT na API do MockAPI destina-se apenas à atualização de recursos já existentes.

Para exemplificar, selecionamos o ID 1 no endereço com /1, enviamos uma requisição PUT para /api/cursos/1, alteramos o título para "Curso de API 2" e removemos a descrição, conforme a seguir:


Copiar
{
  "titulo": "Curso de API 2"
}

Ao clicarmos em "Send", todos os outros dados permanecerão intactos e apenas o título será alterado:


Copiar
{
    "data_criacao": "2024-05-10T17:01:53.539Z",
    "titulo": "Curso de API 2",
    "descricao": "Curso sobre padrões de API",
    "id": "1"
}

Essa API não está seguindo exatamente o que o método PUT deveria realizar.

De acordo com a especificação do HTTP, o método PUT exige o envio do recurso completo. Se o recurso não existir, ele será criado. Se já existir, será substituído. Em suma, o PUT é usado para atualização ou criação completa do recurso conforme necessário.

No entanto, é importante destacar que a maioria das APIs não seguem esse padrão. Utilizar o método PUT corretamente é essencial. Por quê? Se desejamos atualizar apenas o título, como fizemos agora, não devemos usar o método PUT, mas sim o** método PATCH**.

Note que em "Method Definitions" na documentação não encontramos informações sobre o método PATCH.

Explorando o método PATCH

O PATCH é discutido em outra RFC. Portanto, pesquisaremos por "http patch" no navegador. Isso nos fornecerá várias páginas. Escolheremos a da MDN, que é uma documentação oficial da web. Clicamos no menu do lado direito em "Especificações". Isso nos mostrará a especificação do PATCH, que é a RFC 5789.

Esse método permite realizar alterações parciais. Semelhante ao PUT, o PATCH atualiza um recurso existente de forma parcial.

Se uma requisição PATCH for feita para um recurso inexistente, como no exemplo da rota /cursos/2, a atualização não ocorrerá. Ao contrário, o PUT criaria o recurso se não existisse. Portanto, o PATCH é usado exclusivamente para atualizações parciais de recursos.

Se desejamos modificar apenas um campo do curso, usamos o PATCH. Contudo, a Mock API não adota esse padrão ou definição do HTTP.

Removendo recursos com DELETE

O método DELETE é utilizado para remover um recurso específico. Ao enviar uma requisição DELETE para /api/cursos/1, o curso correspondente será removido e não estará mais disponível. Se tentarmos realizar um GET posteriormente, receberemos um erro indicando que o curso não existe mais.

Something went wrong while parsing response JSON

Da mesma forma, se tentarmos listar todos os cursos com /cursos, veremos que a lista está vazia:

[]

Portanto, o método DELETE é eficaz para remover permanentemente um recurso.

Método CONNECT

O método CONNECT é pouco utilizado em APIs, sendo principalmente destinado a estabelecer conexões diretas com o servidor.

Método OPTIONS

Já o método OPTIONS é semelhante ao HEAD, mas com uma finalidade distinta. Enquanto o HEAD é uma variação do GET que solicita apenas os cabeçalhos da resposta, o OPTIONS é usado para receber as informações de um servidor sobre o que ele suporta em um determinado endpoint.

Isso significa que ao enviar uma requisição OPTIONS, estamos focados apenas nos cabeçalhos da resposta. Para exemplificar, voltamos ao Postman e alteramos o método para OPTIONS e clicamos em "Send".

Observe na parte inferior que não há corpo na requisição. Clicando em "headers", o objetivo é entender quais cabeçalhos o endpoint espera receber e quais URLs têm permissão de acesso.

Deixaremos um "Para saber mais" com um link para mais informações sobre o cabeçalho CORS, que possibilita o acesso a outros endereços para nossa API. Então, um serviço acessa o outro.

Este cabeçalho permite especificar quais métodos HTTP são suportados por nossa API. Note que o HEAD não está incluído nesta lista "Access-Control-Allow-Methods". Portanto, esses são os cabeçalhos suportados por nossa API: GET, PUT, POST, DELETE e OPTIONS.

O método OPTIONS é usado para obtermos informações sobre o que é permitido nesta API.

É muito utilizado pelo navegador quando fazemos requisições via JavaScript. O navegador, de forma assíncrona, envia primeiro uma requisição OPTIONS para verificar se pode enviar a requisição com corpo, recuperar a resposta e outras informações necessárias.

Verbo vs. Método

É possível que tenha notado que às vezes falamos em "método" e outras em "verbo HTTP". Em português, ambos os termos são usados, mas em inglês é mais comum e usualmente se usa apenas "HTTP method", não "HTTP verb". Por isso, nos acostumamos a usar principalmente "método". No entanto, "verbo HTTP" também é uma terminologia aceita e amplamente utilizada.

Conclusão e Próximos passos

Entendemos os diferentes tipos de requisição e os métodos definidos no protocolo HTTP. Agora vamos explorar as propriedades específicas de cada um desses métodos, pois cada um deles se encaixa em categorias importantes ao desenvolvermos uma API.

No próximo vídeo, discutiremos essas propriedades em detalhes!

@@02-Para saber mais: especificações
DISCUTIR NO FÓRUM
Durante a aula, analisamos algumas especificações oficiais do protocolo HTTP. A primeira é sobre conteúdo e semântica e a segunda é específica sobre o método PATCH.

https://datatracker.ietf.org/doc/html/rfc9110

https://datatracker.ietf.org/doc/html/rfc5789

@@03-Para saber mais: CORS
DISCUTIR NO FÓRUM
Um dos problemas mais comuns ao consumirmos APIs em aplicações Web é o problema de CORS: Cross-origin resource sharing. O método OPTIONS é utilizado pelo navegador exatamente para obter informações sobre acesso a recursos a partir de origens diferentes.

No vídeo a seguir o problema é explicado e sua solução também é apresentada:

https://www.youtube.com/watch?v=Fha6Il-5RYE&source_ve_path=MjM4NTE&embeds_referring_euri=https%3A%2F%2Fcursos.alura.com.br%2F

@@04-Propriedades dos métodos

No último vídeo, aprendemos sobre os métodos HTTP e o significado de cada um deles. Compreendemos os propósitos individuais deles. No entanto, cada um desses propósitos possui certas características.

Ao retornar à RFC, acessando o menu à direita, encontramos a tabela de conteúdos e a seção 4.2, "Common Method Properties". Clicando nela, observamos que cada método pode ser safe (seguro), idempotent (idempotente) e cacheable (cacheável).

Vamos agora entender o que esses termos significam.

Safe Methods

Primeiramente, um método considerado seguro significa que não realizará alterações no servidor. Em essência, é um método read-only ("somente leitura"). Ele não adiciona, atualiza nem remove dados.

Exemplos de métodos read-only incluem GET, que é seguro, assim como HEAD e OPTIONS. Por outro lado, POST, PUT, PATCH e DELETE não são métodos seguros, pois modificam ou removem dados.

Métodos seguros devem ser reservados exclusivamente para operações de leitura.

Criar uma API que utilize o verbo GET para inserir ou remover informações é contraproducente e inadequado.

Quando recuperamos uma informação, inserimos um log (um efeito colateral que o cliente não precisa saber), mas a expectativa do cliente é que o método seja seguro e assume que pode chamar esse método de forma indiscriminada.

Portanto, ele não se preocupará com a segurança das informações. Consequentemente, métodos seguros não devem ser usados para ações potencialmente destrutivas ou que custem e armazenem dados.

Por exemplo: quando há um link em uma página web que utiliza o verbo GET, toda vez que digitamos uma URL no navegador, estamos utilizando o método GET. Os motores de busca, como o Google, ao visitarem nossa página e encontrarem uma requisição GET, entendem que podem acessá-la livremente para rastreá-la.

Caso fosse um formulário que utilizasse o método POST, o Google não o enviará. Os rastreadores de motores de busca evitam enviar formulários porque sabem que não é um método seguro.

Se sabemos que a ação não é destrutiva, podemos utilizar o método seguro; no entanto, se estamos removendo ou inserindo algo, não devemos usar um método seguro.

Voltamos à documentação para entendemos sobre idempotentes methods.

Idempotentes methods

Um método é considerado idempotente quando o efeito no servidor, ao receber múltiplas requisições seguidas e idênticas à primeira, produz o mesmo resultado que apenas uma requisição única.

Assim, ao realizarmos várias vezes uma requisição GET, o resultado esperado será consistente. Já ao efetuar múltiplas requisições POST, o resultado pode variar (um novo recurso com id ou data de criação diferente sendo criado). No caso de requisições PUT, espera-se que sejam idempotentes, pois são destinadas à atualização completa do recurso.

Em outras palavras, enviar a requisição uma ou várias vezes significa que o recurso está sendo armazenado como novo ou atualizado com todos os dados, resultando na mesma ação.

Uma requisição do tipo DELETE é idempotente porque, após ser enviada, espera-se que o recurso não exista mais no servidor. No Postman, optamos pelo método DELETE com o endereço /api/cursos/1. Ao clicarmos em "Send" sete vezes, o recurso não continuará não existindo.

Not found

Assim, o conceito de idempotência se refere à capacidade de uma requisição produzir o mesmo resultado esperado, independentemente de ser enviada uma vez ou várias vezes.

Observe que o retorno não precisa ser idêntico, pelo menos não conforme a especificação. O que precisa ser idêntico é o resultado esperado. Portanto, um método não precisa ser seguro para ser idempotente, mas um método seguro é idempotente. Isso ocorre porque podemos chamá-los várias vezes e obteremos sempre o mesmo resultado esperado.

Ao enviarmos sete requisições do tipo PUT para /api/cursos/2, esperamos obter o recurso do tipo curso com ID 2 contendo todos os dados enviados na requisição. Apesar de a API da MockAPI não seguir rigorosamente o método HTTP como deveria, essa é a essência de um método idempotente.

Portanto, é crucial que ao modelarmos nossa API, tornemos os métodos idempotentes verdadeiramente idempotentes. Devemos ter em mente que um cliente HTTP espera que múltiplas requisições PUT resultem no mesmo efeito: um único registro no banco de dados com as informações enviadas.

No caso do método PATCH, ao enviarmos uma atualização apenas para o título e não para outras informações de /api/cursos/2, não podemos garantir que o recurso permanecerá no mesmo estado. Isso ocorre porque, mesmo que tenhamos a descrição "teste" e acabemos de alterar o título, enviar essa requisição várias vezes não garante que a descrição permanecerá inalterada. Por isso, não é um método idempotente.

Vamos aos métodos cacheáveis.

Cacheable methods

Alguns métodos permitem que suas requisições sejam armazenadas para acesso mais rápido, o que melhora a performance. O navegador utiliza essas informações para determinar o que pode ou não ser armazenado em cache.

Métodos cacheáveis asseguram que requisições futuras não precisem acessar novamente o servidor, utilizando o que já está armazenado.

Um exemplo é o método GET, que pode ser cacheável. Ao enviar uma requisição para obter todos os cursos em /api/cursos, nosso cliente pode optar por armazenar essa resposta em cache, dependendo das informações disponíveis.

[]

Quando repetimos essa requisição, o cliente pode responder utilizando o que já está armazenado, sem precisar consultar o servidor. Geralmente, requisições do tipo POST não são cacheáveis, exceto em algumas situações específicas.

Respostas para uma requisição do tipo POST só podem ser cacheadas se incluírem explicitamente informações de freshness (como se fosse a novidade dessa informação). A documentação contém especificações sobre como calcular o freshness de um recurso.

Portanto, por padrão, não é possível armazenar em cache, pois sempre é necessário acessar o servidor para criar um novo recurso.

Deixaremos uma tabela com todos os métodos seguros, idempotentes e cacheáveis para consulta.

Ao desenvolver uma API, é crucial considerar os diferentes tipos de métodos. O cliente pode armazenar em cache algumas requisições, então é importante entender se uma requisição do tipo POST pode ser cacheada na API, e enviar as informações corretas. Requisições do tipo GET geralmente são cacheadas, e devemos incluir as informações de cache apropriadas.

E essas informações são enviadas nas respostas. Além do corpo, a resposta pode conter outras informações adicionais.

Próximo passo

No próximo vídeo, abordaremos a resposta, já que dedicamos bastante tempo à requisição. Exploraremos os status de respostas HTTP!

@@05-Para saber mais: tabela de propriedades dos métodos
DISCUTIR NO FÓRUM
Confira a tabela com o resumo das propriedades de cada método HTTP:

Método	Seguro	Idempotente	Cacheável
GET	Sim	Sim	Sim
POST	Não	Não	*
PUT	Não	Sim	Não
DELETE	Não	Sim	Não
PATCH	Não	Não	*
HEAD	Sim	Sim	Sim
OPTIONS	Sim	Sim	Não
* Cacheável somente se a resposta tiver definido explicitamente informações de quão recente é a informação (freshness) e um cabeçalho Content-Location for definido para o mesmo valor da URL acessada.

Informações de freshness podem ser fornecidas através de cabeçalhos como Expires ou Cache-Control: max-age.

https://datatracker.ietf.org/doc/html/rfc9111#name-freshness

@@06-Cache de POST
DISCUTIR NO FÓRUM
João está implementando um endpoint que receberá uma requisição usando o verbo POST para criar uma notificação. Se uma notificação com as informações enviadas já tiver sido criada nos últimos 30 segundos, ela não precisa ser enviada de novo, logo, uma resposta em cache pode ser utilizada pelo cliente.

Quais informações João precisa fornecer na resposta desse endpoint POST para que o cliente saiba que pode cachear a resposta?

Selecione uma alternativa:

A
O cabeçalho Content-Location apontando para o próprio endereço desse endpoint POST.


B
Informações explícitas de freshness como os cabeçalhos Expires ou Cache-Control: max-age.


Informações de freshness e o cabeçalho Content-Location apontando para o mesmo endpoint.

Ao fornecer de forma explícita informações de freshness através de um cabeçalho Expires, por exemplo, e também indicar que Content-Location é o próprio endereço desse endpoint, a API indica que a requisição POST pode ser armazenada em cache.


D
Requisições POST nunca são armazenadas em cache, então não há o que João possa fazer para ajudar o cliente.

@@07-Status de resposta

Após abordarmos amplamente a requisição, os métodos e o corpo em si, agora vamos focar nas respostas.

No Postman, estamos com o método GET em /api/cursos e o seguinte body:


Copiar
{
  "titulo": "Curso de API 2"
}

Ao buscarmos todos os cursos, obtemos um curso incluído. Analisando na parte inferior, podemos observar que o curso possui todos os detalhes padrão.

A resposta inclui um status que identifica seu estado na parte superior direita da resposta. Nele, podemos verificar a resposta HTTP completa, que possui um código indicando seu estado, seja indicando sucesso, problema ou necessidade de ação.

Status 200 OK

O status mais comum é o 200, indicando OK. Ao fazemos uma requisição pelo navegador para acessar um site e conseguimos visualizá-lo, o status da resposta recebida é 200.

Alteramos o método para DELETE e adicionamos /1 (o ID do curso) ao endereço para remover o curso. Ao tentarmos remover clicando em "Send", o curso é excluído e recebemos o status 200.

Status 404 Not Found

Se tentarmos remover o mesmo curso novamente clicando em "Send", o recurso não será mais encontrado, resultando no status 404 Not Found. Ao acessar uma URL inexistente pelo navegador, o status 404 é retornado, indicando um problema do lado do cliente.

O servidor está funcionando conforme esperado, mas o cliente tenta acessar um recurso que não foi encontrado.

Status 201 CREATED

Agora vamos tentar criar um novo recurso para verificar outro status possível. Passamos um título, "Curso de API", e uma descrição, "Descrição teste".

POST


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos


Copiar
{
  "titulo": "Curso de API",
  "descricao": "Descrição teste"
}

Ao enviar esses dados clicando em "Send", o status retornado foi 201, que significa criado. Isso indica que o recurso foi criado com sucesso.

Existem muitos status HTTP e é impossível decorar todos. Lembramos apenas de alguns mais comuns, como 200, 201, 404 e 500, que são respostas frequentes. No entanto, não é necessário decorar todos, pois existem várias tabelas que ajudam a entender quais status são relevantes para cada cenário.

Níveis e Intervalos dos status

É essencial entender os níveis e intervalos de cada status. Nos cenários de sucesso, como OK e criado, os códigos são 200 e algo: 200 para OK e 201 para criado. Em um cenário sem resposta, como ao fazer uma requisição do tipo OPTIONS, não há corpo na resposta.

OPTIONS


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos


Copiar
{
  "titulo": "Curso de API",
  "descricao": "Descrição teste"
}

Observe que ao clicarmos em "Send" obtemos um status 204 No Content.

Um status 204 indica sucesso, mesmo sem conteúdo na resposta. A requisição foi bem-sucedida, então 204 também é uma resposta de sucesso.

Tudo relacionado a sucesso está na faixa 200.

Por outro lado, se tentarmos remover um curso que não existe, como um curso com ID 7, o status retornado estará na faixa 400, indicando erro.

DELETE


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos/7


Copiar
{
  "titulo": "Curso de API",
  "descricao": "Descrição teste"
}

Obtemos como retorno o status 404 Not Found.

Acessaremos novamente a especificação do HTTP. Na seção 6, "Response Status Codes" (Códigos de Status da Resposta), encontramos os códigos de status HTTP da resposta. Os intervalos na faixa de 100, ou seja, aqueles iniciados por 1 seguido por dois outros dígitos, são considerados informativos.

Isso indica que a requisição foi recebida e o processo está em andamento. Em APIs, essa abordagem não é muito comum. É mais utilizada em contextos como versões mais recentes do PHP, onde são oferecidas dicas rápidas ou adiantamentos.

Por exemplo, ao fazer uma requisição para uma página HTTP, ela é recebida e está sendo processada. Durante esse processo, podemos enviar links necessários para o navegador, como para a página de estilo ou arquivos JavaScript.

Os intervalos na faixa de 200 indicam sucesso, como a criação bem-sucedida sem conteúdo, ou simplesmente "OK". Esta faixa abrange diversos tipos de status.

Erros do Cliente e do Servidor

Na faixa de 300, os intervalos representam redirecionamento, que pode ocorrer quando um recurso é movido ou temporariamente redirecionado. Por outro lado, os intervalos na faixa de 400 sinalizam erros do cliente, como requisições com dados inválidos, corpo mal formatado, recursos inexistentes ou excesso de requisições simultâneas.

A faixa de erros do servidor é identificada como 500. Portanto, situações como desconexão, problemas de rede e erros não especificados que ocorrem do lado do servidor são categorizados nesta faixa.

Na especificação, há uma lista completa de todos os status, incluindo páginas que usam cachorrinhos de forma humorística para representá-los. Por exemplo, o HTTP status dogs utiliza imagens de cachorro para ilustrar cada status.

O status OK é representado por um cachorro feliz. O 404 é representado por um cachorro cavando algo e não encontrando nada. Se você prefere gatos, também existe o "HTTP status cats" para isso.

Existem diversos status disponíveis e cada um possui sua própria representação. O status 304, "não modificado", indica que a requisição pode ser atendida através de cache, sem necessidade de resposta direta ao usuário.

O status 400 indica uma "requisição mal feita" ou bad request, enquanto o status 401 significa "não autorizado".

É crucial compreender o significado de cada intervalo de status. Como clientes HTTP, é essencial tratá-los adequadamente para evitar confundir erros da pessoa usuária com erros do servidor. Quando desenvolvemos uma API, é importante utilizar esses status de forma correta.

Voltamos ao Postman.

Ao tentar criar um curso sem enviar todos os dados obrigatórios (embora no nosso caso todos sejam opcionais), é necessário que nossa API responda com o status 400, indicando o erro do cliente.

É bastante comum em desenvolvimento de APIs retornar uma resposta de erro utilizando o status OK. Isso pode complicar a vida do cliente, como já visto em memes e tweets, onde o retorno é marcado como OK, mas o corpo da resposta contém um erro e uma mensagem de erro.

Isso torna a vida do cliente mais complicada e dificulta o uso da API. É fundamental utilizar os status corretos nas respostas para garantir uma interação eficiente.

Conclusão e Próximos passos

Já discutimos bastante sobre a requisição e a resposta. Agora, vamos abordar um conceito presente em ambos: os cabeçalhos. Como podemos e devemos utilizar cabeçalhos a nosso favor ao criar ou consumir APIs? Vamos explorar isso na próxima aula!

@@08-Atenção aos cabeçalhos

Discutimos bastante sobre requisições e respostas, agora abordaremos os cabeçalhos.

Introdução aos Cabeçalhos

Os cabeçalhos permitem a comunicação tanto na requisição quanto na resposta, além do corpo. Por exemplo, em uma requisição utilizando o método GET, não enviamos um corpo. Para isso, selecionamos "none" no body.

Nesse cenário, como especificamos que queremos buscar um curso com o ID 7 e aceitamos receber a resposta em formato JSON? Da mesma forma, ao responder com um curso no formato JSON, como indicamos o formato? Como especificamos essas informações?

Para obter informações adicionais sobre a requisição ou a resposta, utilizamos cabeçalhos HTTP. Ao realizar uma requisição para buscar um curso com o ID 7, precisamos entender quais cabeçalhos devemos enviar. Para isso, podemos utilizar o método OPTIONS.

OPTIONS


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos/7

Clicamos em "Send".

Quando fazemos requisições através do navegador usando JavaScript, o método OPTIONS é automaticamente utilizado para verificar se podemos realizar a requisição. Às vezes, isso pode resultar em problemas de CORS (Cross-Origin Resource Sharing).

Em suma, solicitamos todas as opções disponíveis, incluindo os cabeçalhos (aba "Headers"). Porém, algumas informações retornadas na resposta podem não ser úteis para nós, como detalhes específicos sobre o servidor, por exemplo.

O campo "Access-Control-Allow-Origin" é importante. Este servidor ou API aceita requisições de qualquer origem, domínio ou sistema. Suporta métodos como GET, PUT, POST, DELETE e OPTIONS, além de permitir os seguintes cabeçalhos: Content-Type, que especifica o tipo de dados no corpo da requisição; Cache-Control, que permite detalhar informações de cache na requisição; e Access_token.

No entanto, não podemos especificar para essa API o tipo de dados que esperamos receber em resposta. Ela simplesmente irá ignorar essa informação. Podemos demonstrar isso claramente.

Para isso, buscamos todos os cursos fazendo uma requisição GET para /api/cursos, onde o corpo contém um array em formato JSON.

GET


Copiar
https://663f92fbe3a7c3218a4d6d9d.mockapi.io/api/cursos


Copiar
{
  "data_criacao": "2024-05-11T12:53:33.283Z",
  "titulo": "Curso de API",
  "descricao": "Descrição teste",
  "id": "1"
}

Acesso aos cabeçalhos da requisição

Agora vamos acessar os cabeçalhos da requisição. No Postman, estão localizados abaixo do campo de endereço, em "Headers". Existe um cabeçalho chamado Accept; vamos desmarcá-lo e criar um novo logo abaixo de Connection.

Cabeçalho Accept

O cabeçalho Accept indica o tipo de conteúdo que esperamos na resposta. Especificamente, desejamos receber dados no formato XML, então vamos configurá-lo para text/xml.

[check] Accept: text/xml
Quando enviamos essa requisição clicando em "Send", a API a ignora porque, na resposta do tipo OPTIONS, ela indicou que não suporta o cabeçalho Accept. Portanto, não podemos usá-lo; ele será ignorado.

Quando uma API pode lidar com mais de um formato de dados, muitos frameworks de criação de APIs já oferecem suporte padrão para isso. O cabeçalho Accept é responsável por indicar ao servidor qual formato de dados o cliente espera receber.

Na resposta, na aba "Headers", especificamos o "Content Type" como "application/json", sendo o formato que retornamos.

Esperávamos XML no nosso caso, mas a API ignora esse cabeçalho. Portanto, nos retorna informando que se trata de um JSON. Se fosse um HTML, como em páginas da web, seria text/xml.

Portanto, o Content Type nos diz qual o tipo dos dados no corpo da requisição ou resposta. Enquanto o Accept identifica o que esperamos receber, porém, essa API não suporta esse cabeçalho.

Cabeçalho de cache

Outro detalhe muito importante são os cabeçalhos de cache: Cache-Control. Essa API não retorna os detalhes de cache.

Ao retornarmos uma informação de cache, indicamos como o cliente pode armazená-la e se é permitido. Se houver um intermediário entre o servidor e o cliente, como um servidor de cache ou uma CDN, esse servidor intermediário utiliza esse cabeçalho para decidir se pode armazenar a resposta em cache.

Teremos um "Para Saber Mais" dedicado ao CACHE HTTP, incluindo um exemplo prático com um servidor web para ilustrar seu funcionamento.

Uso do Etag para cache

Outra opção é o Etag. O Etag também é utilizado para armazenar cache. É uma maneira do servidor informar ao cliente quando o recurso foi modificado, indicando se precisamos atualizá-lo.

Para determinar se um recurso precisa ser atualizado, verificamos o cabeçalho da resposta. Se necessário, fazemos a requisição utilizando o método HEAD, que busca o recurso sem retorná-lo no corpo da resposta completa.

Isso economiza largura de banda e processamento. Se o recurso foi modificado, então fazemos uma nova requisição usando o método GET.

Importância dos Cabeçalhos

Os cabeçalhos desempenham um papel importante ao comunicar intenções e transmitir informações tanto na requisição quanto na resposta. Os cabeçalhos mais utilizados são os de formato e cache.

Próximos passos

Agora que já exploramos bastante o protocolo HTTP, abordaremos padrões de desenvolvimento de APIs. Como as APIs eram tradicionalmente criadas? E como são criadas hoje em dia? Quais são outros formatos além daqueles que estamos abordando aqui?

Então a próxima aula será sobre padrões de APIs!

@@09-Para saber mais: Cache HTTP

Em diversos momentos da aula o conceito de cache foi citado. No vídeo a seguir você vai conferir um exemplo prático de cache sendo utilizado pelo navegador para armazenar uma imagem e evitar uma requisição:


Uma API deve fornecer as informações corretas para que os clientes saibam se podem realizar cache ou não. Nem todo cliente tem a capacidade de realizar cache, mas o servidor precisa prover as informações. Postman e Insomnia são bons exemplos de clientes HTTP que não realizam cache. Já o navegador é um bom exemplo de cliente que armazena cache.

https://www.youtube.com/watch?v=IrwIYywpvbM&source_ve_path=MjM4NTE&embeds_referring_euri=https%3A%2F%2Fcursos.alura.com.br%2F&embeds_referring_origin=https%3A%2F%2Fcursos.alura.com.br

@@10-Mão na massa: pratique o uso de HTTP
DISCUTIR NO FÓRUM
Nesta aula, nós conhecemos a especificação do protocolo HTTP e entendemos como ele pode ser utilizado em APIs.

Agora é sua vez! Chegou a hora de você praticar o uso do que o protocolo HTTP pode oferecer. Utilize a API de exemplo e leia as especificações citadas na aula para fixar os conceitos.

Opinião do instrutor
•

Opções
Acesse a especificação do protocolo HTTP e consulte a parte dos métodos;
Realize diferentes requisições para a API de exemplo;
Analise os cabeçalhos (das requisições e das respostas) e os status das respostas.

https://datatracker.ietf.org/doc/html/rfc9110#name-methods

@@11-O que aprendemos?
DISCUTIR NO FÓRUM
Nesta aula, nós:

Conhecemos mais a fundo sobre o protocolo HTTP, inclusive lendo a especificação oficial do protocolo;
Aprendemos as propriedades de cada método (ou verbo) HTTP, entendendo quais são seguros, idempotentes e cacheáveis;
Conhecemos os status de resposta do protocolo HTTP, entendendo o que cada intervalo quer dizer;
Entendemos a importância dos cabeçalhos e como eles normalmente podem ser utilizados por APIs.


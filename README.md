## Projeto Stranger Things

> Décimo projeto do módulo de Back-end do curso de desenvolvimento web da Trybe.

**Contexto**

No bloco desse projeto aprendemos a realizar o deploy do front-end e back-end de nossas aplicações utilizando o `Heroku`.
Diferentemente dos projetos anteriores, o código desse projeto foi inteiramente desenvolvido pela `Trybe`. 
Nosso objetivo se resume a modificar o valor de algumas variáveis, definir variáveis de ambiente e configurar o deploy da aplicação.

**Objetivo do projeto**

Adaptar e configurar o deploy do front-end e back-end de uma aplicação utilizando a plataforma do `Heroku` e o gerenciador de processos `PM2`.

**Principais habilidades desenvolvidas nesse trabalho**

  - Publicar aplicações através do `Heroku`;
  - Visualizar logs das suas aplicações publicadas;
  - Monitorar suas aplicações publicadas;
  - Utilizar variáveis de ambiente dentro do `Heroku`;
  - Instalar, utilizar e aproveitar os principais recursos do `PM2`;
  - Fazer deploy no `Heroku` aproveitando recursos de um process manager.

**Tecnologias utilizadas**
- <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/javascript/javascript-original.svg" title="JavaScript" align="center" height="30"/> - JavaScript</a>
- <a href="https://nodejs.org"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/nodejs/nodejs-original.svg" title="Node.js" align="center" height="35"/> - Node.js</a>
- <a href="https://expressjs.com"><img src="https://images.tute.io/tute/topic/express-js.png" title= "Express" align="center" height="35"/> - Express</a>
- <a href="https://reactjs.org/"><img src="https://raw.githubusercontent.com/devicons/devicon/master/icons/react/react-original-wordmark.svg" title="React" align="center" height="35"/> - React</a>
- <a href="https://heroku.com"><img src="https://www.vectorlogo.zone/logos/heroku/heroku-icon.svg" title="Heroku" align="center" width="30" height="30"/> - Heroku</a>

**Deploy**

Deploy do front-end da aplicação: https://willian-prado-pd.herokuapp.com/.

Deploy do back-end da aplicação:
  * Modo normal: https://willian-prado-bd.herokuapp.com/
  * Modo *upside-down*: https://willian-prado-bk.herokuapp.com/

---

### Descrição da aplicação

 - #### Back-end
  
  Uma API simples com um único endpoint `/` que retorna uma listagem com os personagens da série **Stranger Things**.
  A lista de personagem possui os seguintes campos:
  
     name: Nome do personagem;
     status: se o personagem está vivo ou não na série. Os valores possíveis são `alive`, `deceased` ou `unknown`;
     origin: o local de origem do personagem.
     
   Um query string pode ser usada com qualquer um dos campos para filtrar resultados. A busca é case insensitive.
   Ex: 
   > localhost:3000?name=el

  Na API, no arquivo `index.js`, há a seguinte variável de controle:
    
    const hereIsTheUpsideDown = true;
  
  Caso seu valor seja `true`, a API irá retornar os dados dos personagens de ponta-cabeça.

  - #### Front-end

  O frontend consiste em um projeto simples utilizando React. Ele possui as seguintes funcionalidades:

   - Uma tabela para exibição da resposta da nossa API;
   - Um campo de pesquisa para filtro de **nome**;
   - Botões de navegação para paginação;
   - Um botão para ativar o modo `Mundo Invertido` no frontend.

  Todas essas funcionalidades estão implementadas no componente `StrangerThings`.
  
  O botão para o modo `Mundo Invertido` altera a API que está sendo chamada para obter os dados dos personagens, alterando também a imagem
  do background da aplicação.

---

### Lista de requisitos propostos pela Trybe:

### Backend

#### 1 - Verifica as variáveis de ambiente

Altere o backend para utilizar variáveis de ambiente para contrololar os seguintes comportamentos:

   1. A porta que a API escutará, essa variável deve ter, nescessariamente, o nome PORT e o seu valor deve ser 3000.

   2. O modo "upsideDown". Essa variável espera um valor boleano e deverá se chamar UPSIDEDOWN_MODE. Lembre-se que as variáveis de ambiente são `strings`.

**Importante**: Para esse projeto, as variáveis de ambiente devem ser definidas em um arquivo .env e o arquivo deve ser enviando no seu PR(Pull Request). ISSO NÃO É UMA PRÁTICA DE MERCADO, o arquivo .env deve ser sempre incluido do .gitignore pois contém informações sensíveis, aqui será enviado apenas por motivo de avaliação.

#### 2 - Verifica se o módulo pm2 foi instalado no projeto

Adicione o módulo PM2 à API.

#### 3 - Verifica a configuração do ecosystem.config.yml

Adicione o arquivo `ecosystem.config.yml`. O arquivo deverá realizar as seguintes configurações:

  1. Ativar o Modo Cluster;
  2. Subir duas instâncias do processo;
  3. Não assistir à alterações no diretório (modo`watch` desativado);
  4. Reiniciar o processo caso ele consuma mais de 200MB de memória.
  **importante**: O arquivo `ecosystem` deve ter a extensão yml e não yaml.

#### 4 - Verifica se os scripts do package.json estão corretos

Adicione/altere dois `scripts` no `package.json`:

  1. `start`: Deverá iniciar o server utilizando o módulo do `PM2` e apontando para o arquivo `ecosystem` criado;

  2. `start:dev`: Deverá iniciar o server utilizando o módulo do `PM2`, **sem** apontar para o arquivo `ecosystem` e com o parâmetro para "observar alterações no diretório" **ativado**.

Execute ambos em sua máquina para validar se o comportamento é o esperado.

#### 5 - Verifica a configuração do arquivo Procfile

Defina um arquivo `Procfile`, utilizando a mesma configuração do script `start` do `package.json`: iniciar o server utilizando o módulo do `PM2`, apontando para o arquivo `ecosystem` criado anteriormente.

Lembre-se: como nossos serviços receberão acessos HTTP externos, precisamos definir os `Dynos` como sendo do tipo `web`.

#### 6 - Verifica o Deploy no Heroku

**IMPORTANTE**: Uma variável de ambiente com o nome GITHUB_USER deverá ser criada com o seu usuário do github.

**IMPORTANTE**: O heroku limita o tamanho do nome de uma aplicação para ter no máximo **30 caracteres**, se o seu usuário do GitHub possuir mais que 27 caracteres você não conseguirá criar uma aplicação com o nome no padrão solicitado pelo requisito. Caso esteja nessa condição, avise nosso time de instrução que iremos ajudá-lo.

1. Crie dois `apps` do Heroku a partir do mesmo código fonte (código da API). O nome do seu app no heroku deverá conter seu nome de usuário no github seguido de "-bk" ou "-bd". Por exemplo, se seu nome de usuário no github for "student" seus app deverão ter o nome "sudent-bk" e "student-bd" e as urls abaixo:

   - https://student-bk.herokuapp.com/ -para o app hawkins

   - https://student-bd.herokuapp.com/ -para o app upside-down

2. Configure a variável de ambiente criada para controlar o modo `upsideDown`. Cada um dos `apps` deverá ter valores distintos, da seguinte maneira:

   - O app `hawkins` deverá ter o valor `false`;

   - O app `upside-down` deverá ter o valor `true`.

3. Utilizando o `git`, faça o deploy de ambos os `apps` no Heroku.

Acesse os URLs geradas e valide se ambas as API's estão no ar e funcionando como esperado.
**Importante**: As URLS deverão ser geradas pelo heroku e não devem ser modificadas.

### Frontend

#### 7 - Verifica as variáveis de ambiente do frontend

Altere o frontend para utilizar variáveis de ambiente para controlar as **URLs** e **Timeouts** de comunicação com a API.

Perceba que o código está esperando por duas **APIs**. Uma para o modo `upside-down` e a outra para o modo normal.

O nome das variáveis deve ser o seguinte:

- Para seu back-end hawkins:
  - REACT_APP_HAWKINS_URL para a URL;
  - REACT_APP_HAWKINS_TIMEOUT para o timeout;

- Para seu back-end UPSIDEDOWN:
  - REACT_APP_UPSIDEDOWN_URL para a URL;
  - REACT_APP_UPSIDEDOWN_TIMEOUT para o timeout;

#### 8 - Verifica se foi feito o deploy do frontend no Heroku

**IMPORTANTE**: Assim como no backend, a variável de ambiente GITHUB_USER

deverá ser criada com o seu usuário do github.

Faça o deploy do front-end:

   1. Crie um app do Heroku com o front-end. Não é necessário a criação do `Procfile` aqui. Vamos deixar o Heroku utilizar as configurações padrões. No momento de criar o app do Heroku, utilize o `buildpack` descrito abaixo, em **Dicas**.

   2. O nome do seu app no heroku deve ser seu nome de usuário do github seguido de "-ft". Por exemplo, se o seu usuário do github for "student", o nome do seu app será "student-ft" e a url ***precisar ser*** https://student-ft.herokuapp.com/.

   2. Configure as variáveis de ambiente do app para apontar para as API's publicadas.

   3. Faça o deploy com o git.

**Dicas**:

Para publicar seu frontend React, utilize o buildpack [mars/create-react-app](https://elements.heroku.com/buildpacks/mars/create-react-app-buildpack).

Lembre-se de que é possível testar o comportamento definindo as variáveis de ambiente em sua máquina. Você pode fazê-las apontar tanto para o backend rodando localmente em sua máquina, quanto para as APIs já publicadas nos requisitos anteriores.

### Bônus

#### 9 - Verifica os multi-ambientes e modo de desenvolvimento.

Utilize a estratégia de multi-ambientes no frontend. Para isso:

   - Renomeie o *remote* atual para `development`;

   - Refaça o deploy com um item no frontend que identifique o layout como rodando em modo de "desenvolvimento". Esse tag item **deve** conter o texto "Em desenvolvimento"

   - Crie um novo app no heroku cujo nome deve ser seu nome de usuário do github seguido de "-pd". Por exemplo, se o seu usuário do github for "student", o nome do seu app será "student-pd" e a url ***precisar ser*** https://student-pd.herokuapp.com/.

   - Lembre-se que a boa prática para essa situação é criar uma variável de ambiente para controlar esse comportamento, configurando-a para ter um valor diferente em cada um dos ambientes.


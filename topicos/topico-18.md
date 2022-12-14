## [Tópico T18] - Modelo Entidade Relacionamento (MER) - Decisões de Projeto
###### *by Prof. Plinio Sa Leitao-Junior (INF/UFG)* &#9728;

Ao abstrair potenciais elementos conceituais no projeto de banco de dados, a questão inicial é:

| **O *elemento conceitual* é um *tipo de entidade*, *um tipo de relacionamento* ou um *atributo*?** |
| -------------------------------------------------------------------------------------------------- |

```diff
- Há diretrizes para essa tomada de decisão?
+ É preciso estar atento ao significado de cada elemento conceitual ...
```

### Preâmbulo

>**Mudanças** são esperadas e típicas:
- Cada decisão durante o projeto conceitual está sujeita a alterações durante a modelagem.<br>
Por exemplo, um **elemento conceitual** inicialmente categorizado como ***atributo*** pode tornar-se um ***tipo de entidade*** no decorrer do processo, e vice-versa.

>Por se tratar de um **processo interativo, iterativo e evolutivo**, comumente **três aprendizados** são compartilhados:
- A **interação** entre os atores é parte integrante da **elaboração** e da **validação** de cada versão do esquema conceitual.
- Quaisquer **discussões excessivas** sobre *como modelar um elemento conceitual devem ser evitadas*: **iterações porvir** trarão maior clareza para as decisões.
- A sequência de versões em si do esquema conceitual resulta em aprendizado com efeitos positivos para a **evolução do próprio esquema conceitual**.

### Tipo de relacionamento **versus** Atributo ou Tipo de Entidade

> O elemento conceitual representa uma associação com significado entre dois (ou mais) elementos conceituais?
- se sim, é um candidato a TIPO DE RELACIONAMENTO, principalmente se os outros elementos conceituais são *tipos de entidade*:
  - por exemplo, o elemento conceitual cujo significado é **aluno se matricula em turma** é um tipo de relacionamento entre os tipos de entidade cujos significados são **conjunto de alunos** e **conjunto de turmas**, respectivamente.
- se não, é um candidato a ATRIBUTO ou TIPO DE ENTIDADE, conforme o seu significado:
  - por exemplo, o elemento conceitual cujo significado é **conjunto de alunos** é um tipo de entidade;
  - outro exemplo, o elemento conceitual que tem o significado **data de nascimento do aluno** é um atributo do tipo de entidade cujo significado é **conjunto de alunos**.

### Atributo *versus* Tipo de Entidade

> O domínio de valores do elemento conceitual é estável (ou mesmo fixo)?
- Se sim, é um candidato a ATRIBUTO, principalmente se o domínio for fixo:
  - por exemplo, o elemento conceitual cujo significado é **estado civil do funcionário** possui domínio fixo: *&#123; casado, solteiro, ... &#125;*.
- Se não, é um candidato a TIPO DE ENTIDADE, principalmente se for composto e houver pretendente(s) a atributo chave:
  - por exemplo, o elemento conceitual **produto** é composto por _código_, _descrição_ e _preço unitário_, em que _código_ é pretendente natural a atributo chave.

> O elemento conceitual possui vários (dois ou mais) significados, que mencionam outros elementos conceituais?
- Se sim, é um candidato a TIPO DE ENTIDADE, principalmente se os outros elementos conceituais são *tipos de entidade*:
  - os elementos conceituais **departamento do curso de graduação** e **departamento do professor** mencionam os tipos de entidade cujos significados são **conjunto de cursos de graduação** e **conjunto de professores**: neste caso o elemento conceitual em questão é um tipo de entidade cujo significado é **conjunto de departamentos**:
    - neste exemplo, há um tipo de relacionamento binário entre os elementos conceituais cujos significados são:
      - **conjunto de departamentos** e **conjunto de cursos de graduação**; e
      - **conjunto de departamentos** e **conjunto de professores**.
- Se não, é um candidato a ATRIBUTO, principalmente se seu significado menciona um único tipo de entidade:
  - por exemplo, o elemento conceitual cujo significado é **preço unitário do produto** é um atributo do tipo de entidade que tem o significado **conjunto de produtos**.

### Atributo de Tipo de Entidade *versus* Atributo de Tipo de Relacionamento

> O significado do elemento conceitual menciona outros (dois ou mais) elementos conceituais?
- Se sim, é um candidato a ATRIBUTO DE TIPO DE RELACIONAMENTO, principalmente se os outros elementos conceituais são *tipos de entidade*:
  - por exemplo, se o significado do elemento conceitual é a **quantidade de horas semanais que um *funcionário* trabalha em um *projeto***, então este é um atributo do tipo de relacionamento que tem o significado **funcionário trabalha em projeto**.
- Se não, é um candidato a ATRIBUTO DE TIPO DE ENTIDADE, principalmente se o significado menciona um único tipo de entidade:
  - por exemplo, se o significado do elemento conceitual é **a data de pagamento da *fatura***, então este é um atributo do tipo de entidade que tem o significado **conjunto de *faturas***.
- Em ambos os casos, o atributo contribui para o significado do tipo de entidade ou do tipo de relacionamento.

### Atributo Multivalorado *versus* Tipo de Entidade e Tipo de Relacionamento

> O significado do elemento conceitual menciona um outro elemento conceitual e atribui cardinalidade maior do que 1 (um)?
- Se sim, é um candidato a ATRIBUTO MULTIVALORADO, principalmente se for um atributo simples (não composto):
  - por exemplo, o elemento conceitual cujo significado é **telefones celulares do vendedor** é um atributo multivalorado do tipo de entidade que tem o significado **conjunto de vendedores**.
- Se não, é um candidato a TIPO DE ENTIDADE e TIPO DE RELACIONAMENTO, principalmente se for composto e houver pretendente(s) a atributo chave:
  - por exemplo, o elemento conceitual que tem o significado **autores do livro** é composto por _código_, _nome_ e _data de nascimento_, em que _código_ é candidato a atributo chave:
    - neste caso, o elemento conceitual representa:
      - um tipo de entidade (significado **conjunto de autores**); e 
      - um tipo de relacionamento binário (significado **autor do livro**).

## Atividade (data limite: **12/08/2022 23h59min59s**)

Crie o diretório **topico-18** no seu repositório https://github.com/contagithub/bd-2022-1-bia, onde **contagithub** é o nome da conta do aluno no Github. Este é o repositório que você criou no início da disciplina.

Neste diretório você deverá depositar um arquivo JPG, contendo a imagem de um DER conforme solicitado na atividade.<br>
**Atenção às diretrizes abaixo**:
- Use a ferramenta que desejar, desde que a especificação do DER tenha **precisamente** a notação apresentada no [Tópico 15a](./topico-15a.md):
  - Sugestão 1: use a ferramenta [Dia](http://dia-installer.de/), que é uma ferramenta de desenho:
    - para especificar o DER, selecione a *Folha* **ER** (em vez da *Folha* **Banco de Dados**);
  - Sugestão 2: use a ferramenta [ERRCASE](https://sites.google.com/a/cin.ufpe.br/eercase/), que é uma ferramenta de 'modelagem' de banco de dados;
  - Independente da ferramenta utilizada, ao final exporte o desenho para um arquivo JPG.
- Ao 'depositar' o arquivo no diretório, checar se as dimensões da imagem do diagrama estão ajustadas à area de apresentação no GitHub (não deve ser muito pequeno a ponto de tornar-se ilegível, nem grande demais a ponto de ser necessário **rolar** (*to scroll*) para visualizar).
- Faça você mesmo, evite olhar respostas prontas.<br> Novamente, convém citar Cora Coralina para esclarecer o objetivo da atividade: "O que vale na vida não é o ponto de partida e sim a caminhada. Caminhando e semeando, no fim terás o que colher".

A atividade considera os requisitos de dados do **BD Árvore genealógica**, que inclui as seguintes demandas informacionais:
1. Que pessoas são primas em primeiro grau?
1. Que pessoas não possuem filhos ou filhas?
1. Qual o nome dos avós paternos e maternos de uma certa pessoa?
1. Quais o nome das pessoas que faleceram com menos de 20 anos?
1. Para uma dada pessoa, quais o nome e o parentesco dos seus parentes (tais como, filho, pai, avó, prima, primo, tio, tia, etc.)?

Desenhe um DER capaz de atender todas as demandas informacionais acima:<br>
&#9786; É necessário 'desenhar' o DER completo.

UMA RESPOSTA

Uma _possível resposta_ está [aqui](https://github.com/GabrielvanderSchmidt/bd-2022-1-bia/blob/main/topico-18/t%C3%B3pico-18.jpg).

Favor avaliar a sua resposta conforme os pontos abaixo:<br>
1. Toda pessoa deve, necessariamente, ter pai e mãe cadastrados no banco de dados? Se sim, tal tornaria o banco de dados inviável? ([exemplo](https://github.com/ArthurJung/bd-2022-1-bia/blob/main/topico-18/Diagrama1.jpg))
1. Duas pessoas podem ser homônimas? ([exemplo](https://github.com/cachops/bd-2022-1-bia/blob/main/topico-18/DER.jpg))
1. É necessário incluir outros parentescos no banco de dados, além de 'pai' e 'mãe'? ([exemplo](https://github.com/alexandreacff/bd-2022-1-bia/blob/main/T%C3%B3pico%2018/T%C3%B3pico%2018.jpeg))
1. Ao indicar paternidade e maternidade, é requerido indicar o 'papel desempenhado' por cada entidade participante em tipos de relacionamentos recursivos? ([exemplo](https://github.com/cachops/bd-2022-1-bia/blob/main/topico-18/DER.jpg)).
1. A associação de parentesco entre duas pessoas requer tipo de relacionamento com grau maior que dois, tal como ternário? ([exemplo](https://github.com/DecivanDamascenoAraujoFilho/bd-2022-1-bia/blob/main/topico-18/topico_18.png) [exemplo](https://github.com/Fabrycio-Nakano/bd-2022-1-bia/blob/main/topico-18/topico_18.png) <sub>SEM APROVEITAMENTO</sub>)
1. Há redundância entre atributo e tipo de relacionamento (tal como 'chave estrangeira')? ([exemplo](https://github.com/EryKoston/bd-2022-1-bia/blob/main/44444.jpeg) <sub>SEM APROVEITAMENTO</sub>)
1. Ao ter pai, mãe e filho (ou outro parente) em tipos de entidade separadas, foi previsto que pai e mãe são também filho de outras pessoas? Se sim, o esquema promove redundância de dados? ([exemplo](https://github.com/GabrielBarcelos01/bd-2022-1-bia/blob/main/topico-18/BD%20%C3%81rvore%20geneal%C3%B3gica.png) [exemplo](https://github.com/EryKoston/bd-2022-1-bia/blob/main/44444.jpeg) <sub>SEM APROVEITAMENTO</sub>)
1. Tipos de relacionamento que determinam pai e mãe de uma pessoa são redundantes com tipos de relacionamento que estabelecem os filhos (ou outro parentesco) de uma pessoa? ([exemplo](https://github.com/reisguilherme/bd-2022-1-bia/blob/main/Topico%2018/Topico18.png) [exemplo](https://github.com/GO0108/bd-2022-1-bia/blob/main/T%C3%B3pico%2018/T%C3%B3pico%2018.jpg) <sub>SEM APROVEITAMENTO</sub>)
1. Atributos tais como 'parentes', 'filhos' e 'herdeiros' são atributos derivados? ([exemplo](https://github.com/HugoF-Silva/bd-2022-1-bia/blob/main/T%C3%B3picos/T%C3%B3pico%2018/18.jpg) [exemplo](https://github.com/lucasbrandao4770/bd-2022-1-bia/blob/main/topicos/topico-18/T18.jpg))
1. Imagem não renderizável? ([exemplo](https://github.com/omatheusbrandao/bd-2022-1-bia/blob/main/T%C3%B3pico%2018.jpg) <sub>SEM APROVEITAMENTO</sub>)

## Artefatos

1. Diretório **topico-18**, criado no repositório do estudante, contendo um arquivo com a imagem JPG do DER solicitado.

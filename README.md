<h1>Site da 923a (Desenvolvimento de Sistemas)</h1>
<p align="center">
    <img src="https://user-images.githubusercontent.com/87045182/181387130-c456a222-a7eb-4f46-9269-fe333c7d6f44.png" alt="Logo do 3° ano do curso de Desenvolvimento de Sistemas" style="width: 100px">
</p>

![Versão do NPM](https://img.shields.io/badge/npm-v8.15.0-orange) ![Versão do Vue CLI](https://img.shields.io/badge/vue--cli-v5.0.8-blue) ![Status do projeto](https://img.shields.io/badge/status-em%20desenvolvimento-informational)

## Índices
* [Descrição](#descrição)
* [Funcionalidades](#funcionalidades)
* [API](#api)
* [Acesso ao projeto](#acesso-ao-projeto)
* [Rodar o projeto localmente](#rodar-o-projeto-localmente)
* [Técnicas e tecnologias utilizadas](#técnicas-e-tecnologias-utilizadas)
* [Copyright](#copyright)


## Descrição

Uma Aplicação de Página Única (SPA) feita com o objetivo de juntar, em um lugar, as informações da turma 923a (curso de Desenvolvimento de Sistemas, Instituição Federal de Alagoas) e praticar minhas habilidades web usando VueJS.

Teve seu layout pensado pelo método de Mobile First, e consiste em um visual pensado para se relacionar com as cores do curso, tentando-se manter um padrão ou relação entre componentes.

## Funcionalidades

- Func. 1: O programa detecta a plataforma sendo usada (pela propriedade do navegador `navigator.userAgent`) e usa essa informação para esconder, ou não, a barra de navegação do cabeçalho
    - Func. 1.1: Caso a plataforma sendo usada seja mobile e o cabeçalho seja escondido, uma botão de menu será disponibilzado para que se possa abrir a barra de navegação, sendo acompanhado de uma animação suave para deixar a usabilidade mais agradável
- Func. 2: Cada item da barra de navegação te levará para uma seção da página, também personalizado com uma animação, dessa vez de scroll suave, para que o usuário entenda o que está acontecendo
- Func. 3: No momento, a seção de destaque traz a visualização dos uniformes do terceiro ano da nossa turma; ela contém botões que trocam dinamicamente os uniformes sendo exibidos
- Func. 4: O rodapé contém links importantes da instituição que te levarão para os respectivos sites
- Func. 5: É possível cadastrar atividades na seção de Atividades, podendo, assim, juntar todas as atividades da turma em apenas um lugar, tendo em vista que professores diferentes usam plataformas diferentes
    - Func. 5.1: Um ícone de "adicionar" é disponibilizado ao lado do título da seção de Atividades, este abre uma janela modal contendo um formulário especializado para a inclusão de uma nova atividade **(a ideia futuramente é que apenas os representantes tenham acesso a essa funcionalidade)**
    - Func. 5.2: É possível escolher a cor com que a matéria vai ser disponibilizada na página principal com um _color picker_ desenvolvido manualmente
    - Func. 5.3: Caso haja a tentativa de adicionar uma atividade com informações vazias ou inválidas, a janela acusará um erro que será visualizado no rodapé do modal
    - Func. 5.4: Em caso de atividade válida adicionada, a janela modal fechará, e em poucos segundos a seção de atividades atualizará com as novas informações
    - Func. 5.5: É possível deletar uma atividade apertando na pequena lixeira no canto superior direito do cartão de atividade **(para o caso de atividades fora do prazo, a ideia seria que elas fossem removidas automaticamente)**
    - Func. 5.6: As atividades são automaticamente ordenadas pela data mais próxima, trazendo uma organização maior à exibição 
- Func. 6: As atividades que possuírem link para a atividade na plataforma Google Classroom disponibilizarão um ícone no canto superior direito que levará o aluno diretamente para a respectiva atividade (obviamente não funcionará para quem não está na sala correspondente, tendo em vista que a funcionalidade é voltada exclusivamente para os alunos da 923A)

## API

Para a persistência das informações e devido funcionamento do cadastro das atividades, desenvolvi um Serviço Web REST (RESTful Web Service) em Java usando a _framework_ Spring e o banco de dados não relacional MongoDB. Dessa forma, adicionar e visualizar as atividades da turma se torna mais dinâmico e fácil de manter. 

Até o momento, nela é possível coletar as atividades (GET), adicionar novas atividades (POST) e removê-las (DELETE). Falta a funcionalidade UPDATE para se ter um CRUD completo.

O projeto foi armazenado em um repositório separado, e pode ser acessado nesse link: https://github.com/deisantix/api-site-923a

## Acesso ao projeto

Você pode acessar o projeto em modo de produção no seguinte link: https://desenv-sistemas-923a.vercel.app/

Para fazer o deploy foi usado o Vercel CLI. Vercel é uma excelente plataforma para hospedagem de sites de graça (no caso de seu plano básico).

##### :warning: É importante ressaltar que o projeto não sai das margens de diretrizes do uso de uma conta pessoal (plano Hobby) do Vercel, tampouco contém objetivo de ganho financeiro para mim ou qualquer um citado no projeto (a demonstração dos uniformes não deve contar como tal, já que a compra não é feita pelo site, e nenhum de nós recebe retorno financeiro).

O projeto foi, antes do desenvolvimento, desenhado na ferramenta Figma, e pode ser acessado aqui: [Figma do Projeto](https://www.figma.com/file/Ak4NgJobqm6VhVf07iQzFy/site-923a?node-id=0%3A1)

## Rodar o projeto localmente

Para rodar o projeto localmente, certifique de que em sua máquina estão instaladas devidamente as dependências a seguir:
- NodeJs ^16.0.0
- NPM (Node Package Manager) ^8.0.0

### 1. Usando o prompt de comando ou terminal, dê um clone do projeto onde preferir:
```
git clone https://github.com/deisantix/site-923a.git
```
OBS: também é válido baixar o arquivo .zip do projeto e extraí-lo no diretório de preferência.

### 2. Após baixado o projeto, entre no diretório usando a linha de comando:
```
cd site-923a
```
### 3. Você verá que dentro do projeto terá o arquivo `package.json`. Ele é o responsável por instalar as dependências necessárias para a aplicação funcionar. Faça isso usando o simples comando do `npm`:
```
npm install
```

### 4. Assim que finalizadas as instalações, basta rodar o comando a seguir:
```
npm run serve
```

### 5. Vue começará a inicializar seu modo de desenvolvimento, e abrirá um servidor local que poderá ser acessado para visualização em tempo real do projeto. Basta acessar o `localhost` que ele irá disponibizar e pronto! 
Ex.:
```
http://localhost:8080
```

## Técnicas e tecnologias utilizadas:

Para o desenvolvimento do projeto foi usado o editor de código `VSCode` e o framework front-end `VueJS`. Foram utilizadas lógicas de componentes para desenvolver o site e torná-lo mais dinâmico e manutenível.

## Copyright

Não há uma licença para o projeto, porém é de **extrema importância** ressaltar que a logo usada no início desse README, que também foi usada no projeto, não deve ser compartilhada ou usada para fins comerciais, tendo em vista que pertence aos alunos do curso de Desenvolvimento de Sistemas, que financiaram.

### Menção Honrosa: Bruno Lucas dos Santos, que primeiro desenhou o brasão.

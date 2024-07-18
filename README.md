# PROJETO TRYBE GAMES

O projeto Trybe Games foi realizado durante o curso de formação full-stack pela Trybe, na eletiva C#. 

Em um software de gerenciamento de dados de usuários e dos jogos jogados por eles, que já teve o desenvolvimento iniciado, foram criadas diversas consultas `LINQ` e implementados vários métodos de manipulações a coleções já existentes.

## 📖 Habilidades trabalhadas 📖

- Habilidades com relação a manipulação de coleções;
- Desenvolvimento de consultas LINQ para determinadas operações;
- Aplicação de um método de testes sobre coleções;
- Interpretação do funcionamento do código já implementado e das coleções de dados existentes no software;

## 
<details>
<summary><strong>Este sistema está dividido em diretórios específicos:</strong></summary><br>

 - 📝 `Contracts/`: Estão armazenadas as `interfaces` que uma classe pode implementar.
 - 🎮 `Controller/`: Estão armazenados os controllers responsáveis por realizar alguma ação que interage com a pessoa usuária e o banco de dados. Neste caso há apenas um _controller_.
 - 🔒 `Database/`: Está armazenada a classe que representa o banco de dados do sistema. Essa classe contém uma lista de cada um dos modelos presentes no sistema e alguns métodos que podem ser utilizados para fazer consultas a essas listas e a relações entre elas.
 - 🖥️ `Models/` Contém os Modelos do sistema, no caso três: `Game`, `Player`, `GameStudio`.
  
</details>

O arquivo `Program.cs` utiliza a classe `TrybeGamesController` para executar as ações com a pessoa usuária, então é possível ver o sistema em funcionamento ao executar o projeto em `src/TrybeGames` com o comando `dotnet test`.

Cada `Game` possui duas relações com `Player`:
 1. Um jogo `Game` pode ter várias pessoas jogadoras `Player` utilizando para isso o membro `Game.Players`, que é uma lista do tipo inteiro e armazena os Ids das pessoas jogadoras.
 2. Uma pessoa jogadora `Player` pode ter vários jogos `Game` comprados utilizando para isso o membro `Player.GamesOwned`, que é uma lista do tipo inteiro e armazena os Ids dos jogos comprados.

`GameStudio`, por sua vez, se relaciona apenas com `Game`. Cada `Game` é desenvolvido por um `GameStudio` e é utilizado o campo `Game.DeveloperStudio`, que é do tipo inteiro e armazena o Id do studio desenvolvedor do jogo.

Cada `Player` também pode ter uma lista de estúdios favoritos. Para isso é utilizado o seu membro `Player.FavoriteGameStudios`, que é uma lista do tipo inteiro que armazena os Ids dos estúdios favoritos.

Esses Models, por sua vez, são utilizados na classe `TrybeGamesDatabase` para compor o banco de dados. E `TrybeGamesDatabase` é utilizado em `TrybeGamesController` para realizar as consultas e operações requisitadas pela pessoa usuária. Abaixo, o diagrama completo com todas as relações entre cada entidade do sistema.

<details>
<summary>Diagrama</summary>

![complete-diagram](https://github.com/user-attachments/assets/bbd4dcd5-f151-4f0d-ae92-05fa2b77ecab)

</details>

## IMPLEMENTAÇÕES REALIZADAS

### 1. Adicionar uma nova pessoa jogadora ao banco de dados

_Método `AddPlayer()` no arquivo `src/TrybeGames/TrybeGamesController.cs`_

- Utiliza as entradas da pessoa usuária pelo <code>Console</code> para criar uma nova pessoa jogadora e adicionar ao banco de dados

### 2. Adicionar um novo estúdio de jogos ao banco de dados

_Método `AddGameStudio()` no arquivo `src/TrybeGames/TrybeGamesController.cs`_

- Utiliza as entradas da pessoa usuária pelo <code>Console</code> para criar um novo Estúdio de Jogos e adicionar ao banco de dados

### 3. Adicionar novo Jogo ao Banco de dados

_Método `AddGame()` no arquivo `src/TrybeGames/TrybeGamesController.cs`_

- Utiliza as entradas da pessoa usuária pelo <code>Console</code> para criar um novo Jogo e adicionar ao banco de dados

### 4. Buscar jogos desenvolvidos por um estúdio de jogos

_Método `GetGamesDevelopedBy()` no arquivo `src/TrybeGames/Database/TrybeGamesDatabase.cs`_

- Recebe por parâmetro um estúdio de jogos e retorna todos os jogos que aquele estúdio desenvolveu

### 5. Buscar jogos jogados por uma pessoa jogadora

_Método `GetGamesPlayedBy()` no arquivo `src/TrybeGames/Database/TrybeGamesDatabase.cs`_

- Recebe por parâmetro uma pessoa jogadora e retorna todos os jogos jogados por aquela pessoa jogadora

### 6. Buscar jogos comprados por uma pessoa jogadora

_Método `GetGamesOwnedBy()` no arquivo `src/TrybeGames/Database/TrybeGamesDatabase.cs`_

- Recebe por parâmetro uma pessoa jogadora e retorna todos os jogos que aquela pessoa jogadora possui

### 7. Buscar todos os jogos junto do nome do estúdio desenvolvedor

_Método `GetGamesWithStudio()` no arquivo `src/TrybeGames/Database/TrybeGamesDatabase.cs`_

- Este método não recebe parâmetros e retorna as informações de jogos e seus estúdios de acordo com o DTO GameWithStudio

### 8. Buscar todos os diferentes Tipos de jogos dentre os jogos cadastrados

_Método `GetGameTypes()` no arquivo `src/TrybeGames/Database/TrybeGamesDatabase.cs`_

- Este método não recebe parâmetros e retorna as informações dos tipos de jogos dentre os jogos cadastrados

### 9. Buscar todos os estúdios de jogos junto dos seus jogos desenvolvidos com suas pessoas jogadoras

_Método `GetStudiosWithGamesAndPlayers()` no arquivo `src/TrybeGames/Database/TrybeGamesDatabase.cs`_

- Este método não recebe parâmetros e retorna as informações dos estúdios de jogos, seus jogos e para cada jogo, suas pessoas jogadoras de acordo com os DTOs StudioGamesPlayers e GamePlayer

### 10. Testes da funcionalidade de buscar jogos jogados por uma pessoa jogadora

_Método `TestGetGamesPlayedBy()` no arquivo `src/TrybeGames.Test/TestTrybeGamesDatabase.cs`_

- Implementa o teste relativo ao método GetGamesPlayedBy()

## ©️ DISCLAIMER

<div align="justify">
Com exceção das alterações destacadas acima no tópico "implementações realizadas", <b>TODOS OS DEMAIS ARQUIVOS</b> foram desenvolvidos e estão sob responsabilidade da TRYBE, incluindo, mas não se limitando ao: código inicial pré-implementado, models, database, diagrama entidade-relacionamento do sistema e demais diretórios necessários para o funcionamento da aplicação.
</div>

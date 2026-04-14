# EntrePares 1.0
## Alunos participantes
* Daniel Bueno Lacerda
* Guilherme Paiva Nabak
* Luiz Felipe Clemente Machado
* Pedro Maia Machado Hernandes

## Professor responsavel
* Marcos Andre Silveira Kutova

<br>

## 📝 Descrição do Sistema
EntrePares 1.0 é um sistema de console voltado para o gerenciamento de cursos livres ofertados por alunos. Desenvolvido em Java, o projeto permite que usuários se cadastrem, realizem autenticação por email e senha, criem múltiplos cursos e gerenciem suas informações, incluindo descrição, data de início e estado atual. Cada curso pode ser compartilhado externamente por meio de um código alfanumérico único, facilitando sua divulgação.

O sistema segue o padrão de arquitetura MVC, separando claramente as responsabilidades entre interface, controle e acesso a dados. A persistência é realizada por meio de arquivos binários, utilizando um CRUD com registros estruturados em bytes. Para garantir eficiência nas operações, são empregados índices em Hash Extensível para acesso direto às entidades e Árvores B+ para gerenciar o relacionamento entre usuários e cursos.

## ✨ Principais Funcionalidades
#### Para Usuários

* **Autenticação Segura:** Cadastro e login de usuários utilizando email e senha. As senhas são armazenadas por meio de hash, garantindo maior segurança dos dados.
* **Gerenciamento de Conta:** Usuários podem visualizar e alterar seus dados pessoais, incluindo nome, email, pergunta e resposta secreta e senha.
* **Recuperação de Senha:** Caso o usuário esqueça sua senha, o sistema permite redefini-la por meio da validação da pergunta e resposta secreta cadastradas.
* **Validação de Exclusão:** Um usuário não pode ser removido do sistema caso possua cursos ativos vinculados. Caso possua apenas cursos inativos, estes são removidos juntamente com a conta.

#### Para Cursos

* **CRUD Completo:** Criação, leitura, atualização e exclusão de cursos associados ao usuário logado.

* **Vinculação Automática:** Todo curso criado é automaticamente associado ao usuário ativo no sistema, garantindo o relacionamento 1:N entre usuário e cursos.

* **Estrutura do Curso:** Cada curso possui nome, descrição detalhada, data de início, estado (ativo, encerrado, concluído ou cancelado) e um código compartilhável único.

* **Geração de Código Único:** Cada curso recebe automaticamente um código alfanumérico de 10 caracteres (estilo NanoID), utilizado para compartilhamento externo.

* **Gerenciamento de Estado:** O usuário pode alterar o estado do curso ao longo do tempo, podendo encerrar inscrições, concluir ou cancelar o curso, respeitando as regras de transição definidas pelo sistema.

* **Listagem Organizada:** Os cursos do usuário são exibidos em ordem alfabética, facilitando navegação e seleção no menu.

* **Acesso por Código:** O sistema permite a identificação de cursos por meio do código compartilhável, possibilitando sua divulgação fora do sistema.

## 🏗️ Estrutura do Projeto

O projeto é organizado em pacotes que separam as responsabilidades, seguindo o padrão Model-View-Controller.

* **`Entidades` (Model):** Representa o núcleo do Modelo, contendo as classes que definem os objetos de negócio do sistema e como eles são persistidos em disco.
    * **`Usuario.java`**: Modelo de entidade Usuário, com atributos como ID, nome, e-mail, hash da senha para segurança, além de pergunta e resposta secreta para recuperação de conta.
    * **`Curso.java`**: Modelo de entidade Curso, com atributos como ID, ID do usuário (proprietário), nome, descrição, data de início, estado (ativo/concluído) e um código compartilhável único (NanoID).


## 🖥️ Telas do Sistema

1. **Menu Inicial** <br> ![1](Imagens/Menu%20Inicial.png) <br>
2. **Cadastro Novo Usuário** <br> ![2](Imagens/Cadastro%20de%20Novo%20Usuario.png) <br>
3. **Login** <br> ![3](Imagens/Tela%20de%20Login.png) <br>
4. **Menu Principal(Pós-Login)** <br> ![4](Imagens/Menu%20Principal.png) <br>
5. **Meus Dados** <br> ![5](Imagens/Tela%20meus%20dados.png) <br>
6. **Meus Cursos** <br> ![6](Imagens/Tela%20meus%20cursos.png) <br>
7. **Adicionar Novo Curso** <br> ![7](Imagens/Tela%20de%20adicionar%20novo%20curso.png) <br>
8. **Alterando Dados do Curso** <br> ![8](Imagens/Alterando%20dados%20do%20curso.png) <br>
9. **Curso Concluído** <br> ![9](Imagens/Concluido%20curso.png) <br>
10. **Curso Excluído** <br> ![10](Imagens/Curso%20excluido.png) <br>
11. **Detalhes de Um Curso** <br> ![11](Imagens/Detalhes%20de%20um%20curso%20selecionado.png) <br>
12. **Encerrando Inscrições** <br> ![12](Imagens/Encerrando%20inscricoes.png) <br>


## ✅ Checklist de Avaliação
### TP_1

> **Há um CRUD de usuários (que estende a classe ArquivoIndexado, acrescentando Tabelas Hash Extensíveis e Árvores B+ como índices diretos e indiretos conforme necessidade) que funciona corretamente?**
>
> Sim. A classe ArquivoUsuario.java gerencia o CRUD de usuários. Ela utiliza um índice de Hash Extensível (indiceIndiretoEmail) para o e-mail, permitindo que a autenticação (login) seja feita de forma eficiente sem percorrer todo o arquivo de dados.

> **Há um CRUD de cursos (que estende a classe ArquivoIndexado, acrescentando Tabelas Hash Extensíveis e Árvores B+ como índices diretos e indiretos conforme necessidade) que funciona corretamente?**
>
> Sim. A classe ArquivoCurso.java gerencia o CRUD de cursos. Ela utiliza uma Árvore B+ para organizar os cursos por usuário e uma Tabela Hash Extensível para a busca rápida através do código compartilhável (NanoID).

> **Os cursos estão vinculados aos usuários usando o idUsuario como chave estrangeira?**
>
> Sim. A classe Curso.java possui o atributo idUsuario, que atua como chave estrangeira, garantindo o relacionamento de integridade entre as entidades no sistema de arquivos.

> **Há uma árvore B+ que registre o relacionamento 1:N entre usuários e cursos?**
>
> Sim. A classe ArquivoCurso.java utiliza uma ArvoreBMais<ParUsuarioCurso>, que armazena pares (idUsuario, idCurso). Isso permite recuperar instantaneamente a lista de todos os cursos pertencentes a um usuário específico.

> **Há um CRUD de usuários (que estende a classe ArquivoIndexado, acrescentando Tabelas Hash Extensíveis e Árvores B+ como índices diretos e indiretos conforme necessidade)?**
>
> Sim. A classe ArquivoUsuario.java utiliza uma Tabela Hash Extensível como índice indireto para o e-mail, permitindo buscas e logins rápidos sem percorrer o arquivo principal.

> **O trabalho compila corretamente?**
>
> Sim. O projeto foi estruturado com pacotes e compilado sem erros a partir do diretório raiz.

> **O trabalho está completo e funcionando sem erros de execução?**
>
> Sim. Todas as funcionalidades descritas no escopo do TP1 foram inovadoras e testadas, funcionando conforme o esperado e com tratamento de abordagens para uma execução estável.

> **O trabalho é original e não a cópia de um trabalho de outro grupo?**
>
> Sim. O trabalho foi desenvolvido pelos participantes listados, com base nas estruturas de dados fornecidos e nos requisitos do anunciado.





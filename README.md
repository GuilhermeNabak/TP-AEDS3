# Gestão de inscrição em cursos livres
## Alunos participantes
* Daniel Bueno Lacerda
* Guilherme Paiva Nabak
* Luiz Felipe Clemente Machado
* Pedro Maia Machado Hernandes

## Professor responsavel
* Marcos Andre Silveira Kutova

<br>

## 📝 Descrição do Sistema
Gestão de inscrição é um sistema de console voltado para o gerenciamento de cursos livres ofertados por alunos. Desenvolvido em Java, o projeto permite que usuários se cadastrem, realizem autenticação por email e senha, criem múltiplos cursos e gerenciem suas informações, incluindo descrição, data de início e estado atual. Cada curso pode ser compartilhado externamente por meio de um código alfanumérico único, facilitando sua divulgação.

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

## 🖥️ Telas do Sistema

## ✅ Checklist de Avaliação
### TP_1

> **Há um CRUD de usuários (que estende a classe ArquivoIndexado, acrescentando Tabelas Hash Extensíveis e Árvores B+ como índices diretos e indiretos conforme necessidade) que funciona corretamente?**
>
> 

> **Há um CRUD de cursos (que estende a classe ArquivoIndexado, acrescentando Tabelas Hash Extensíveis e Árvores B+ como índices diretos e indiretos conforme necessidade) que funciona corretamente?**
>
> 

> **Os cursos estão vinculados aos usuários usando o idUsuario como chave estrangeira?**
>
> 

> **Há uma árvore B+ que registre o relacionamento 1:N entre usuários e cursos?**
>
> 

> **Há um CRUD de usuários (que estende a classe ArquivoIndexado, acrescentando Tabelas Hash Extensíveis e Árvores B+ como índices diretos e indiretos conforme necessidade)?**
>
> 

> **O trabalho compila corretamente?**
>
> 

> **O trabalho está completo e funcionando sem erros de execução?**
>
> 

> **O trabalho é original e não a cópia de um trabalho de outro grupo?**
>
> 





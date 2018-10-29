# Criando um bom Pull Request

## Como contribuir 

Antes de abrir o Pull Request ou quando estiver fazendo um Code Review, execute um check-list com todos itens abaixo.

Se o Pull Request não atender algum dos requisitos definidos neste guideline, ele não pode ser mergeado.

### Check-list

* A mensagem dos _**commits**_ deve descrever de maneira clara o contexto/porquê daquela alteração. No artigo [How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/) tem algumas boas práticas para escrever uma boa mensagem de commit.
* A descrição do _**pull request**_ deve conter o problema de negócio e técnico. Explicar a solução adotada, deixando bem claro porque da alteração.
* Ter pelo menos um approve do mantenedor do time responsável;
* Se o _**pull request**_ for feito em par, o par não pode dar approve.
* O _**pull request**_ só pode ter uma responsabilidade, se conter mais, deve-se abrir em mais _**pull requests**_.
* O _**pull request**_ não pode ser mergeado se tiver algum -1 \(ou change-request\). Todos os comentários devem ser respondidos e/ou resolvidos.
* O _**pull request**_ precisa ao menos um approve, podendo ser ou não do mantenedor \(podendo mudar por time\);
  * Caso o mantenedor ou o responsável pelo _**pull request**_ achar necessários mais approves, aguardar até que possua.
* Caso por algum motivo a equipe precise de uma regra mais restritiva para os membros, o mantenedor \(ou grupo de mantenedor\) do time tem liberdade de colocar para o próprio time;
* _**Pull request**_ só é considerado aprovado quando o mantenedor der o _approve_, mas para ele dar o approve ele vai esperar a quantidade e qualidade de _**Code Reviews**_ que ele julgar ser necessário para aquele PR.
  * Por exemplo, num _**pull request**_ grande, o mantenedor pode esperar por ter mais _**code reviews**_  para depois ele dar o OK. Num _**pull request**_ pequeno de pouco impacto na aplicação, o mantenedor pode ele mesmo dar OK sem precisar de _**code review**_ de ninguém.

## Responsabilidade de um mantenedor

* Todo PR precisa de approve de apenas um mantenedor de cada contexto;
  * Se o time achar que não é necessário, não siga este ponto, apenas os do approve;
* Caso por algum motivo o time precise de uma regra mais restritiva para os membros, o mantededor do time tem liberdade de colocar;
* O mantenedor também é responsável pelo PR.

## O que você deve avaliar em um Pull Request?

**Design**

* O código segue boas práticas, como [Clean Code](https://de.wikipedia.org/wiki/Clean_Code), [DRY](https://en.wikipedia.org/wiki/Don't_repeat_yourself) e [SOLID](https://en.wikipedia.org/wiki/SOLID).
* O código segue as convenções de código e arquitetura estabelecida pelo time?
* O código segue as convenções da linguagem? \( Exemplo para Java: [Java Code Conventions](http://www.oracle.com/technetwork/java/codeconventions-150003.pdf), [Google Java Style](https://google.github.io/styleguide/javaguide.html) \)
* O código está com a abstração correta? Se estiver utilizando herança, está utilizando ela corretamente?
* O código está no lugar correto?
* Quando existe mais de um padrão, o novo código está seguindo o padrão atual? O código está migrando para o padrão correto ou seguindo o padrão antigo?
* O novo código não poderia reaproveitar código já existente? Está introduzindo código duplicado? Não poderia ser refatorado para um padrão reutilizável?
* O código pode estar introduzindo problemas de segurança para a aplicação?
* O código está adicionando funcionalidades que ainda não são necessárias? O código não pode ser simplificado?
* Existem códigos não utilizados que poderiam ser removidos?
* Quando adicionado uma nova dependência, realmente é necessário?
* Exceções estão sendo tratadas corretamente?
* Se foi criada uma nova dependência com um serviço externo, foi tomado o cuidado necessário para que uma eventual queda, lentidão ou mal-funcionamento do serviço externo não afete o sistema dependente?

**Performance**

* O código pode estar introduzindo problemas de performance?
* O código utiliza as estruturas de dados corretas para aquele cenário?
* O código realiza muitas consultas custosas ao banco de dados?

**Legibilidade e Manutenibilidade**

* Os nomes de classes, métodos, atributos, variáveis, parâmetros e afins refletem as coisas que elas representam?
* Eu consigo entender o que o código faz lendo ele?
* Eu consigo entender o que os testes fazem?
* As mensagens de erros são entendíveis?

**Funcionalidade**

* O código está fazendo o que ele supostamente deveria fazer?
* Existem algum possível bug "oculto" como por exemplo checar uma variável errada ou utilizar um operador de comparação errado?
* As mensagens de usuários estão escritas corretamente?
* Existem erros óbvios que irão quebrar o ambiente de produção?

**Testes**

* Os testes cobrem uma boa quantidade de cenários? Cobrem cenários felizes e casos de exceção? Existem casos que não foram considerados e deveriam ter sido considerado?
* Existem testes que garantem que o código está realizando corretamente sua função? O teste está realmente testando os critérios de aceitação daquela funcionalidade?




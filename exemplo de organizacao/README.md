# Métodos Avançados de Programação

## UNIESP Faculdades

### Professora

* Drª Alana Morais ([alanamm.prof@gmail.com](mailto:alanamm.prof@gmail.com))

### Aluno
* Sirak Leite da Silva Filho ([sirakiesp@gmail.com] (mailto:sirakiesp@gmail.com))


### Padrão Comportamental: 
COMMAND


## Padrão COMMAND

### Problema: 

- Encapsular uma solicitação como um objeto, permitindo parametrizar clientes com diferentes solicitações, enfileirar ou fazer registro (log) de solicitações e suportar operações que podem ser desfeitas (undo).


### Solução: 

- Especificar, enfileirar e executar solicitações em tempos diferentes;
- Registar e eventualmente desfazer operações realizadas;
- Parametrizar as ações a serem executadas pelos objetos;
- Estruturar um sistema com base em operações de alto nível construídas sobre operações básicas.


### Consequências: 

- Desacopla o objeto que invoca a operação daquele que sabe como executá-lo
- São objetos que podem ser manipulados e estendidos como qualquer outro objeto
- É possível juntar comandos formando um comando composto podendo-se usar o padrão COMPOSITE.
- É fácil acrescentar novos COMMANDS  porque não é necessário mudar classes existentes


### Exemplo: 

IMPLEMENTANDO INTERFACE COMMAND
1-public interface Command {
2-
3-	public void execute();
4-
5-}


IMPLEMENTANDO O COMMAND
1-public class LightOnCommand implements Command { 
2-
3-	Light light;
4-
5-	public LightOnCommand(Light light) {
6-		this.light = light;
7-	}
8-
9-	public void execute() {
10-		light.on();
11-	}
12-}

IMPLEMENTANDO CONTROLE REMOTO QUE INVOCARÁ O COMMAND
1-public class ControleRemoto { 
2-
3-	Command slot;
4-
5-	public ControleRemoto() {
6-	}
7-
8-	public void setCommand(Command command) {
9-		slot = command;
10-	}
11-
12-	public void botaoPressionado() {
13-		slot.execute();
14-	}
15-
16-}

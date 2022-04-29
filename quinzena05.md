# Resumo 5 - Paradigmas de Programação
## Vitor Medeiros
## RA: 11201720112

---

## Semana 9 - Laziness

- A avaliacao da expressao nao acontece, em vez disso, é usada uma referência a essa expressão para que seja avaliada somende quando utilizada em execução
(lembra conceito de lazy load) 

- Funções sprint, length e force

- Haskell tambem faz uso de streams (similar a Java)

- Primo folgado e Fibonacci Preguiçoso sao programas-exemplo da aplicação do conceito de laziness em Haskell (novamente parecido com Laziness de outras linguagems) 


## Semana 10 - Programação Concorrente

- Concorrência: Mais de um processo ocorrendo ao mesmo tempo
- Processos podem compartilhar núcleos
- Threads exploram o conceito de concorrência e permitem uma análise do comportamento de sistemas.

- Command ``takeMVar``: se a thread chamadora (caller) estiver vazia, fica blocked até algo ser inserido.
- Command ``putMVar``: se a thread chamadora (caller) estiver cheia, fica blocked até o uso de takeMVar;

### Operações Assíncronas

- Operações non-blocking: A thread nao aguarda resposta e pode seguir os procedimentos normalmente
- Oposto de comunicação síncrona
- Possui vantagens importantes no contexto de Concorrência.

### Estruturas de Dados Funcionais

- Estruturas de dados persistentes sao aquelas que permitem a existência simultânea de diversas versões da estrutura
- Estruturas de dados efêmeras sao as que permitem a existência de apenas uma versão simultânea da estrutura
- Estruturas de dados funcionais são sempre persistentes. 
- Em Estruturas de Dados Funcionais, elementos afetados são sempre copiados.
- Em Estruturas de Dados Funcionais, elementos não afetados são sempre compartilhados entre suas versões.

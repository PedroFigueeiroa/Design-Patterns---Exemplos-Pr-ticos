# Design Patterns - Exemplos Práticos

## Autor

Pedro Gabriel Figueiroa de Sousa

## LLM utilizada

Os exemplos e explicações deste repositório foram desenvolvidos com auxílio do ChatGPT (OpenAI).

---

# 1. Factory Method (Criacional)

## O que é?

Factory Method é um padrão de projeto utilizado pra criar objetos sem que o código principal precise conhecer detalhes da implementação concreta.

## Problema

Quando um programa cria muitos tipos diferentes de objetos, o código pode ficar cheio de condições (if, switch, etc.), tornando a manutenção difícil.

## Solução

Criar uma classe responsável pela criação dos objetos. Assim, o restante do sistema apenas solicita um objeto à fábrica, sem se preocupar com sua implementação.

## Exemplo

No exemplo deste projeto, uma fábrica cria veículos do tipo Carro ou Moto.

---

# 2. Adapter (Estrutural)

## O que é?

Adapter é um padrão utilizado pra permitir a comunicação entre classes que possuem interfaces incompatíveis.

## Problema

Nem sempre uma biblioteca/componente externo possui os métodos esperados pelo sistema.

## Solução

Criar um adaptador que converta uma interface para outra sem alterar o código original.

## Exemplo

No projeto, uma biblioteca externa fornece dados através de um método diferente do esperado pelo sistema. O adaptador faz essa tradução.

---

# 3. Observer (Comportamental)

## O que é?

Observer é um padrão utilizado pra implementar comunicação entre objetos quando um deles sofre alterações.

## Problema

Diversos objetos precisam ser avisados quando ocorre uma mudança em outro objeto.

## Solução

Criar uma lista de observadores que serão notificados automaticamente sempre que houver uma atualização.

## Exemplo

No projeto, um jornal notifica todos os inscritos quando uma nova notícia é publicada.

---

# Linguagem utilizada

Python 3

# Padrões implementados:

* Factory Method (Criacional)
* Adapter (Estrutural)
* Observer (Comportamental)

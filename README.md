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

---

from abc import ABC, abstractmethod

# Produto abstrato
class Veiculo(ABC):

    @abstractmethod
    def mover(self):
        pass

# Produtos concretos
class Carro(Veiculo):

    def mover(self):
        return "Carro andando"

class Moto(Veiculo):

    def mover(self):
        return "Moto andando"

# Factory
class FabricaVeiculos:

    @staticmethod
    def criar_veiculo(tipo):

        if tipo.lower() == "carro":
            return Carro()

        elif tipo.lower() == "moto":
            return Moto()

        else:
            raise ValueError("Tipo de veículo inválido")

# Teste
veiculo1 = FabricaVeiculos.criar_veiculo("carro")
veiculo2 = FabricaVeiculos.criar_veiculo("moto")

print(veiculo1.mover())
print(veiculo2.mover())

---

# Classe existente
class BibliotecaExterna:

    def request(self):
        return "Dados recebidos da biblioteca externa"

# Adapter
class Adaptador:

    def __init__(self, biblioteca):
        self.biblioteca = biblioteca

    def requisicao(self):
        return self.biblioteca.request()

# Teste
biblioteca = BibliotecaExterna()
adaptador = Adaptador(biblioteca)

print(adaptador.requisicao())

---

# Observer
class Inscrito:

    def atualizar(self, noticia):
        print(f"Nova notícia recebida: {noticia}")

# Subject
class Jornal:

    def __init__(self):
        self.inscritos = []

    def adicionar_inscrito(self, inscrito):
        self.inscritos.append(inscrito)

    def remover_inscrito(self, inscrito):
        self.inscritos.remove(inscrito)

    def notificar(self, noticia):
        for inscrito in self.inscritos:
            inscrito.atualizar(noticia)

    def publicar_noticia(self, noticia):
        print(f"\nJornal publicou: {noticia}")
        self.notificar(noticia)

# Teste
jornal = Jornal()

usuario1 = Inscrito()
usuario2 = Inscrito()

jornal.adicionar_inscrito(usuario1)
jornal.adicionar_inscrito(usuario2)

jornal.publicar_noticia("Novo padrão de projeto disponível!")

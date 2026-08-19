# Classes e objetos

Classe é um **modelo** para criar objetos. Objeto é algo criado a partir desse modelo.

```ts
class Pessoa {
    nome: string = "João";
}

const pessoa = new Pessoa(); // cria um objeto da classe Pessoa
```

# Atributos e métodos

Atributos são as **características** de um objeto. Métodos são as **ações** que ele pode realizar.

```ts
class Pessoa {
    nome: string = "João"; // atributo

    falar() { // método
        console.log("Olá!");
    }
}
```

# Construtores (constructor)

O `constructor` é executado automaticamente quando criamos um objeto. Ele pode ser usado para definir os valores iniciais.

```ts
class Pessoa {
    nome: string;

    constructor(nome: string) {
        this.nome = nome; // define o nome ao criar o objeto
    }
}

const pessoa = new Pessoa("João");
```

# Instanciação de objetos

É o ato de **criar um objeto** a partir de uma classe. Usamos `new`.

```ts
class Pessoa {
    nome: string = "João";
}

const pessoa = new Pessoa(); // instancia um objeto
```

# Modificadores de acesso (public, private, protected)

Servem para controlar **onde** uma propriedade ou método pode ser acessado.

```ts
class Pessoa {
    public nome = "João"; // pode ser acessado de qualquer lugar
    private idade = 18; // só pode ser acessado dentro da classe
    protected cpf = "123"; // classe e classes filhas podem acessar
}
```

# Propriedades somente leitura (readonly)

`readonly` faz com que uma propriedade **não possa ser alterada** depois de definida.

```ts
class Pessoa {
    readonly cpf = "123456789";
}

const pessoa = new Pessoa();

// pessoa.cpf = "987654321"; // erro, pois é readonly
```

# Métodos estáticos (static)

Um método `static` pertence à **classe**, e não ao objeto. Podemos utilizá-lo sem criar um objeto.

```ts
class Calculadora {
    static somar(a: number, b: number) {
        return a + b;
    }
}

Calculadora.somar(2, 3); // chama o método diretamente pela classe
```

# Propriedades estáticas (static)

Uma propriedade `static` pertence à **classe**, em vez de pertencer a cada objeto.

```ts
class Pessoa {
    static quantidade = 0;
}

Pessoa.quantidade++; // altera a propriedade da classe
```

# Encapsulamento

É o ato de **proteger os dados internos** de uma classe e controlar como eles podem ser acessados.

```ts
class Conta {
    private saldo = 0; // não pode ser acessado diretamente de fora

    depositar(valor: number) {
        this.saldo += valor; // altera o saldo de forma controlada
    }
}
```

# Herança

Permite que uma classe **herde características e métodos** de outra classe.

```ts
class Animal {
    comer() {
        console.log("Comendo");
    }
}

class Cachorro extends Animal {
    latir() {
        console.log("Au au!");
    }
}

const cachorro = new Cachorro();

cachorro.comer(); // herdado de Animal
cachorro.latir(); // próprio do Cachorro
```

# Polimorfismo

Permite que classes diferentes tenham o **mesmo método**, mas com comportamentos diferentes.

```ts
class Animal {
    falar() {
        console.log("Som");
    }
}

class Cachorro extends Animal {
    override falar() {
        console.log("Au au!");
    }
}

class Gato extends Animal {
    override falar() {
        console.log("Miau!");
    }
}
```

# Abstração

É esconder detalhes desnecessários e mostrar apenas o que é **importante para utilizar o objeto**.

```ts
abstract class Animal {
    abstract falar(): void; // define que todo animal deve falar
}
```

# Getters e setters

`get` serve para **pegar** um valor e `set` serve para **alterar** um valor de forma controlada.

```ts
class Pessoa {
    private nome = "";

    get Nome() {
        return this.nome; // pega o nome
    }

    set Nome(novoNome: string) {
        this.nome = novoNome; // altera o nome
    }
}

const pessoa = new Pessoa();

pessoa.Nome = "João"; // setter
console.log(pessoa.Nome); // getter
```

# Classes abstratas (abstract)

Uma classe `abstract` serve como **modelo para outras classes** e não pode ser criada diretamente.

```ts
abstract class Animal {
    comer() {
        console.log("Comendo");
    }
}

class Cachorro extends Animal {}

const cachorro = new Cachorro(); // permitido

// const animal = new Animal(); // não é permitido
```

# Métodos abstratos

São métodos que são declarados, mas não possuem implementação na classe abstrata. As classes filhas precisam implementá-los.

```ts
abstract class Animal {
    abstract falar(): void; // a classe filha deve implementar
}

class Cachorro extends Animal {
    falar() {
        console.log("Au au!");
    }
}
```

# Sobrescrita de métodos (override)

Acontece quando uma classe filha **substitui o comportamento** de um método da classe pai.

```ts
class Animal {
    falar() {
        console.log("Som");
    }
}

class Cachorro extends Animal {
    override falar() {
        console.log("Au au!"); // substitui o método original
    }
}
```

# Sobrecarga de métodos (method overloading)

Permite que um método possa receber **diferentes tipos ou quantidades de parâmetros**.

```ts
class Calculadora {
    somar(a: number, b: number): number;
    somar(a: string, b: string): string;

    somar(a: any, b: any) {
        return a + b;
    }
}

const calculadora = new Calculadora();

calculadora.somar(2, 3); // números
calculadora.somar("Oi ", "João"); // strings
```

# Parâmetros opcionais em métodos

Um parâmetro opcional pode ou não ser informado. Usamos `?`.

```ts
class Pessoa {
    apresentar(nome: string, idade?: number) {
        console.log(nome, idade);
    }
}

const pessoa = new Pessoa();

pessoa.apresentar("João"); // idade não foi informada
pessoa.apresentar("João", 18); // idade foi informada
```

# Parâmetros padrão

Um parâmetro padrão possui um **valor automático** caso nenhum valor seja informado.

```ts
class Pessoa {
    apresentar(nome: string, idade = 18) {
        console.log(nome, idade);
    }
}

const pessoa = new Pessoa();

pessoa.apresentar("João"); // usa 18 como idade
pessoa.apresentar("Maria", 20); // usa 20
```

# Herança simples

É quando uma classe possui **apenas uma classe pai**.

```ts
class Animal {
    comer() {
        console.log("Comendo");
    }
}

class Cachorro extends Animal {
    latir() {
        console.log("Au au!");
    }
}

// Cachorro herda de apenas uma classe: Animal
```

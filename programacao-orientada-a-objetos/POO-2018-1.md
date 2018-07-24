<!-- .slide: data-state="no-toc-progress" --> <!-- don't show toc progress bar on this slide -->

# Programação Orientada a Objetos
<!-- .element: class="no-toc-progress" --> <!-- slide not in toc progress bar -->

[Diego Silva](https://github.com/diego91964) | [online][1] | [src][2]


[1]: https://diego91964.github.io/unipac/poo
[2]: https://github.com/diego91964/unipac/poo

[3]: http://lab.hakim.se/reveal-js/
[4]: https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet



----  ----

# 1. Introdução

Consiste em um paradigma de programação que se baseia na composição e interação
de objetos.

Note:
Os principais aspectos são: Objetos, Classes, Métodos, Instanciação, Reuso, Mensagens, Chamadas de Métodos, Atributos, Variáveis de Instância, Encapsulamento, Herança

----

## História

>"Alan Kay foi a primeira pessoa que teve a visão de representação por objetos,
tal ideia foi vendida para a Xerox que criou a linguagem Smaltalk."

[Fonte: The University of Tennessee](http://web.eecs.utk.edu/~huangj/CS302S04/notes/oo-intro.html)
[Material Complementar](https://www.youtube.com/watch?v=sTX0UEplF54)

Note:
A criação da orientação a objetos foi em 1970.

Inicialmente, as linguagens orientadas a objetos foram criadas
para a modelagem de objetos do mundo real, como:

* Simulações de fábrica
* Simulações de um sistema planetário
* Um PC desktop - objetos representam janelas, documentos, etc.


----

## Objetos

Um objeto possui um conjunto de dados, sendo capaz de armazenar dados e realizar operações com eles.
Não é necessário mostrar como tais operações foram implementadas.

[Material Complementar](https://youtu.be/aR7CKNFECx0)

Note:
Um carro pode ser considerado um objeto. O mesmo possui operações, como:
ligar,freiar, acelerar, abrir vidro, etc.

----

## Classes x Objetos

Para que exista um objeto, é necessário um modelo, a classe é este modelo, ela
define tudo que existe no objeto, até a implementação de suas operações.

Note:
Ainda utilizando o exemplo do carro, a classe consiste no projeto do veículo.

----

## Propriedades de uma Classe

Em uma classe é possível:
* Declarar as variáveis ​​do objeto.
* Declarar as operações do objeto.
* Definir a função que implementa cada uma dessas operações.

Note:
O conjunto de variáveis de uma classe é chamado de variáveis de instância.

----

## Classes para Objetos

Quando um programa quer uma nova instância de um objeto, ele pergunta a classe
apropriada para criar um novo objeto para ele. A classe aloca memória para manter
as variáveis ​​de instância do objeto e retorna o objeto para o programa.

Note:
Cada objeto sabe qual classe criou para que quando uma operação for solicitada
para esse objeto, ele pode procurar na classe a função que implementa essa
operação e chamar essa função.

----

## Herança

Herança consiste em uma forma de agrupar classes em grupo de operações e variáveis
genéricas, reutilizando estes recursos para classes mais específicas.

Note:
Um carro é um veículo. Um veículo tem variáveis genéricas, como cor e modelo. Também
possui operações genéricas, como ligar e desligar. Um caminhão possui carroceria, um
carro não, ou seja, isto são propriedades específicas.


----

## Herança

Uma classe que herda variáveis e operações de uma classe genérica é chamada de
subclasse e a classe genérica é chamada de superclasse.

![](img/heranca.svg)


Note:
A subclasse não pode excluir nenhuma propriedade herdada da superclasse.

----

## Exemplo Herança

<img src="img/heranca.jpg" width="500"/>

[Fonte: Devmedia](http://www.devmedia.com.br/sobrecarga-e-sobreposicao-de-metodos-em-orientacao-a-objetos/33066)

----

## Sobreposição

A subclasse é livre para definir novas funções para essas operações, isso é chamado de
sobreposição.

Note:
* A subclasse pode seletivamente quais funções sobrepõe.
* Todas as funções que não são substituídas são herdadas.

----


## Exemplo de Sobreposição

<img src="img/sobreposicao.jpg" width="500">

[Fonte: Devmedia](http://www.devmedia.com.br/sobrecarga-e-sobreposicao-de-metodos-em-orientacao-a-objetos/33066)



----

## Parâmetro

Uma operação é chamada de método e recebe parâmetros para executar a sequência
de ações.

```
  Carro.setVelocidade(velocidadeAtual);

  #O Parâmetro do método será a velocidade atual.

```

----

## Sobrecarga

Uma sobrecarga de método consiste em manter vários métodos com o mesmo nome, mas
com número de parâmetros diferentes.

```
  Veiculo.setVelocidade(velocidadeAtual);
  Carro.setVelocidade(velocidadeAtual,marcha);
  Caminhao.setVelocidade(velocidadeAtual,marcha,quantidadeDeArReservatorio)


```

----

## Polimorfismo

É caracterizado quando duas ou mais classes distintas têm métodos de mesmo nome,
de forma que uma função possa utilizar um objeto de qualquer uma das classes
polimórficas, sem necessidade de tratar de forma diferenciada conforme a classe do objeto.

Note:
```
public abstract class OperacaoMatematica {
    public abstract double calcular(double x, double y);
}
public class Soma extends OperacaoMatematica {
    public double calcular(double x, double y) {
      return x + y; }
}
public class Subtracao extends OperacaoMatematica {
    public double calcular(double x, double y) {
        return x - y; }
}


```

----

## Sobreposição - Equals

Qual seria o resultado do seguinte código?

```
  public class Pessoa {

  	private String nome;
  	private String cpf;
  	public String getNome() {
  		return nome;
  	}
  	public void setNome(String nome) {
  		this.nome = nome;
  	}
  	public String getCpf() {
  		return cpf;
  	}
  	public void setCpf(String cpf) {
  		this.cpf = cpf;
  	}
  }

  public class Main {

	public static void main(String[] args) {

		  Pessoa p1 = new Pessoa();
		  p1.setNome("joao");
		  p1.setCpf("12312312312");
		  Pessoa p2 = new Pessoa();
		  p2.setNome("joao");
		  p2.setCpf("12312312312");

		  System.out.println(p1.equals(p2));
	}
}

```

** Deveria ser true.

----

## Sobreposição - Equals


Quando executamos 'p1.equals(p2)' como é feita a comparação?


  ```
  public boolean equals(Object object) {
    return this == object;
  }
  ```
<!-- .element: class="fragment" -->

Para garantir a comparação correta entre dois objetos de uma mesma classe, podemos implementar o método equals.

<!-- .element: class="fragment" -->

----

## Sobreposição - Equals

Como exemplo, podemos pensar que duas pessoas são iguais quando possuem o mesmo CPF.

```
public class Pessoa {

	private String nome;
	private String cpf;
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
	public String getCpf() {
		return cpf;
	}
	public void setCpf(String cpf) {
		this.cpf = cpf;
	}

	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Pessoa other = (Pessoa) obj;
		if (cpf == null) {
			if (other.cpf != null)
				return false;
		} else if (!cpf.equals(other.cpf))
			return false;
		return true;
	}

}
```
<!-- .element: class="fragment" -->

----

## Sobreposição - Equals

A comparação do método equais deve seguir algumas propriedades:

* Reflexiva: Para qualquer referência não nula para x, x.equals(x) deve retornar true.
* Simétrica: Para qualquer referência não nula para x e y, x.equals(y) deve retornar true se, somente se y.equals(x) retonar true.
* Transitiva: Se x.equals(y) == true e y.equals(z) == true, então x.equals(z) deve ser true.
* Consistente: Chamadas sucessivas de x.equals(y) devem retornar o mesmo resultado, desde que consistente.
* Para uma referência não nula para x, qualquer chamada x.equals(null) deve retornar false.


----

## Sobreposição - Hashcode

Como podemos melhorar a busca de um objeto ?

Que tal criarmos uma regra para esta organização?
<!-- .element: class="fragment" -->

![](img/hashcode.png)
<!-- .element: class="fragment" -->

----

## Sobreposição - Hashcode

A função hashcode permite organizar os objetos com base em uma função que os tornam únicos. Assim, a busca dos objetos é otimizada. Mas, é importante saber o comportamento desta função para as diferentes estruturas presentes na linguagem Java. [Material Complementar](https://youtu.be/AbRfF3yHB_Y)

```
public class Pessoa {

	private String nome;
	private String cpf;
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
	public String getCpf() {
		return cpf;
	}
	public void setCpf(String cpf) {
		this.cpf = cpf;
	}

	@Override
	public int hashCode() {
		final int prime = 31;
		int result = 1;
		result = prime * result + ((cpf == null) ? 0 : cpf.hashCode());
		return result;
	}

	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Pessoa other = (Pessoa) obj;
		if (cpf == null) {
			if (other.cpf != null)
				return false;
		} else if (!cpf.equals(other.cpf))
			return false;
		return true;
	}
	@Override
	public String toString() {
		return "Pessoa [nome=" + nome + ", cpf=" + cpf + "]";
	}

}

public class Main {

	public static void main(String[] args) {

		  HashSet<Pessoa> hash = new HashSet<>();

		  List<Pessoa> lista = new ArrayList<>();

		  Pessoa p1 = new Pessoa();
		  p1.setNome("joao");
		  p1.setCpf("12312312312");
		  Pessoa p2 = new Pessoa();
		  p2.setNome("maria");
		  p2.setCpf("12312312312");

		  hash.add(p1);
		  hash.add(p2);

		  lista.add(p1);
		  lista.add(p2);

		  System.out.println("Resultado Hash");
		  hash.stream().forEach(System.out::println);

		  System.out.println("------------------------------\n");

		  System.out.println("Resultado Lista");
		  lista.stream().forEach(System.out::println);

	}

```


----


## Sobreposição - Finalize

Este método é chamado quando um objeto é destruído. Sobrepor este método pode ser uma ação perigosa, pois,
está diretamente ligado a limpeza de memória da JVM. Além disso, o mesmo tende a não se tornar deprecated.

[Material Complementar](http://www.baeldung.com/java-finalize)


----

## Sobreposição - Clone

Este método é responsável por retornar uma cópia do objeto x. Esta cópia deve ter os atributos com os mesmos valores de x, porém,
não necessáriamente o mesmo endereço de memória. Por exemplo:

```
public class Pessoa {

	private String nome;
	private String cpf;
	public String getNome() {
		return nome;
	}
	public void setNome(String nome) {
		this.nome = nome;
	}
	public String getCpf() {
		return cpf;
	}
	public void setCpf(String cpf) {
		this.cpf = cpf;
	}

	@Override
	public int hashCode() {
		final int prime = 31;
		int result = 1;
		result = prime * result + ((cpf == null) ? 0 : cpf.hashCode());
		return result;
	}

	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		Pessoa other = (Pessoa) obj;
		if (cpf == null) {
			if (other.cpf != null)
				return false;
		} else if (!cpf.equals(other.cpf))
			return false;
		return true;
	}
	@Override
	public String toString() {
		return "Pessoa [nome=" + nome + ", cpf=" + cpf + "]";
	}
	@Override
	protected void finalize() throws Throwable {
		System.out.println("Destruindo o objeto:" + this.cpf);
		super.finalize();
	}
	@Override
	protected Object clone() throws CloneNotSupportedException {
		Pessoa aux = new Pessoa();
		aux.setCpf(this.cpf);
		aux.setNome(this.nome);
		return aux;
	}


}

public class Main {

	public static void main(String[] args) {


		try {
			Pessoa p1 = new Pessoa();
			p1.setNome("joao");
			p1.setCpf("12312312312");

			System.out.println("Original:" + p1);
			System.out.println("Clone:" + p1.clone());
			System.out.println("== " + (p1 == p1.clone()));
			System.out.println("equals " + (p1.equals(p1.clone())));


		} catch (CloneNotSupportedException e) {
			e.printStackTrace();
		}

	}
}


```

----

## Encapsulamento

Significa juntar o programa em partes, o mais isoladas possível.
A ideia é tornar o software mais flexível, fácil de modificar e de criar novas implementações.

----

## Mensagens e Chamadas de Método

Um objeto conversa com outro através de mensagens. Estas mensagens são as chamadas de métodos.


----

## Interface

Uma interface consiste em uma coleção de assinaturas de métodos. Uma classe que implementa
uma interface deverá implementar todos os seus métodos.



----  ----

# 2. Introdução à Linguagem

A linguagem utilizada para esta disciplina será Java.

----

## Princípio do Java

> write once run anywhere

![](img/wora.png)

----

## Instalação JRE

[Windows](https://www.java.com/en/download/help/download_options.xml#windows)

[Mac](https://www.java.com/en/download/help/download_options.xml#mac)

[Linux](https://www.java.com/en/download/help/download_options.xml#linux)

[Solaris](https://www.java.com/en/download/help/download_options.xml#solaris)

[Material Complementar](https://www.youtube.com/watch?v=yWU5bm_pZzY)

----

## Instalação JDK

  [Win, Mac, Unix, etc](http://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html)

----

## JDK vs JRE

O próprio nome já da uma dica:
- JDK (Java Development Kit)
- JRE (Java Runtime Environment)

[Devmedia](http://www.devmedia.com.br/instalacao-e-configuracao-do-pacote-java-jdk/23749)

Note:
A Linguagem Java é distribuída em dois grandes pacotes. O primeiro pacote, chamado JRE (Java Runtime Environment), é responsável por permitir que aplicações escritas em Java sejam executadas e deve ser instalado em computadores que não serão utilizados para desenvolvimento de softwares Java.

O segundo pacote, chamado JDK (Java Development Kit), é o pacote que contem toda a infraestrutura necessária para o desenvolvimento de aplicações Java. Ao ser instalado, o JRE é instalado automaticamente.

----

## Bibliotecas

O Java permite que você crie bibliotecas para a linguagem, ajudando assim no reuso de tecnologia.

> As bibliotecas são conhecidas como Java APIs (Application Programming Interfaces)

----

## Ambientes de Programação

* [Eclipse](www.eclipse.org)
* [NetBeans](www.netbeans.org)
* [IntelliJ IDEA](www.jetbrains.com)

> Para esta disciplina utilizaremos o Eclipse.

----

## Fases de um Programa (1)

1. Criar o código fonte (Editor)

```

package br.unipac

public class OlaUnipac {

    public static void main(String[] args) {
        System.out.println("OlaUnipac");
    }

}
```

----

## Fases de um Programa (2)

2. Compilando o programa em Bytecodes

```
  javac OlaUnipac.java
```

----

## Fases de um Programa (3)

3. Executando o software (Invocação da JVM)


```
  java OlaUnipac

```

----

## Fases de um Programa (4,5)

4. Adiciona o arquivo '.class' na memória primária
5. Verifica se o bytecode esta correto

Note:
À medida que as classes são carregadas, o verificador bytecode examina seus bytecodes
para certifique-se de que eles são válidos e não violam as restrições de segurança do Java.

----

## Fases de um Programa (6)

6. Execução do Programa

[Material Complementar](https://www.youtube.com/watch?v=v_ZCtgwbS3o)
[Material Complementar](https://www.youtube.com/watch?v=ijXXaIYsVx4)

Note:
As JVM de hoje geralmente executam bytecodes usando uma combinação de interpretação
e a chamada compilação JIT (just-in-time). Nesse processo, a JVM analisa os bytecodes
à medida que são interpretados. Assim, um compilador Just-in-time (JIT), como o compilador
Java HotSpotTM da Oracle, traduz os bytecodes no idioma da máquina do computador subjacente.
Quando a JVM encontra partes já compiladas, será mais rápido executar tal código.
Assim, os programas Java passam por duas fases de compilação, uma em que o código-fonte
é traduzido em bytecodes (para portabilidade em JVMs em diferentes plataformas de computador)
e um segundo, no qual, durante a execução, os bytecodes são traduzidos para o idioma da máquina
que executa o programa.

----

## Função Main

A primeira função a ser executada em um programa escrito em Java será a função Main.

```
    public static void main(String[] args)
```

Note:
O Java possui algumas palavras reservadas, ou seja, não podem ser utilizada para nomear
classes, métodos e variáveis. São elas:

abstract, boolean, break, byte, case, catch, char, class, const, continue, default, do, double, else, extends, final, finally, float, for, goto, if, implements, import, instanceof, int, interface, long, native, new, package, private, protected, public, return, short, static, strictfp, super, switch, synchronized, this, throw, throws, transient, try, void, volatile, while, assert e enum.

----  ----

# Revisão: Estruturas

Assim como outras linguagens, a linguagem Java possui diversas estruturas de controle e repetição.
Uma grande diferença para a linguagem C seria a estrutura foreach.

----

## Estruturas de Controle

As estruturas de controle são responsáveis por alterar o fluxo do programa se baseano em condições.

----

## Equal vs ==

Quando a comparação '==' é utilizada, apenas o que está 'escrito' é comparado. O método equals compara
realmente o valor que está no objeto. Assim como toString, é possível implementar o método equals em uma classe.


```


public class MainEqual {

	public static void main(String[] args) {

		String s1 = new String( "teste" );
        String s2 = new String( "teste" );

        System.out.println( s1 == s2 );
        System.out.println( s1.equals( s2 ));

	}
}



```


----

## Equal vs ==

```

public class ClasseA {

    public String s;
    public static String s2  = "teste2";

    ClasseA() {
        this.s = new String( "teste" );
    }
}



public class MainEqual {

	public static void main(String[] args) {

		String s1 = new String( "teste" );


        ClasseA a1 = new ClasseA();
        ClasseA a2 = new ClasseA();

        System.out.println( a1 == a2 );
        System.out.println( a1.s == a2.s );
        System.out.println( ClasseA.s2 == ClasseA.s2 );
        System.out.println( a1.s.equals( a2.s ) );

	}
}

```

----

## Equal vs ==

```

public class ClasseB {

	 public String s;

	 ClasseB() {
	        this.s = new String( "teste" );
	    }


	@Override
	public boolean equals(Object obj) {
		if (this == obj)
			return true;
		if (obj == null)
			return false;
		if (getClass() != obj.getClass())
			return false;
		ClasseB other = (ClasseB) obj;
		if (s == null) {
			if (other.s != null)
				return false;
		} else if (!s.equals(other.s))
			return false;
		return true;
	}


}

public class MainEqual {

	public static void main(String[] args) {

        ClasseB b1 = new  ClasseB();
        ClasseB b2 = new  ClasseB();

        System.out.println( b1 == b2 );
        System.out.println( b1.equals(b2));
	}
}




```

----

## Condição IF

A estrutura IF assim como em Java, utiliza uma condição booleana para controlar o fluxo do código, mas,
é importante lembrar que em Java existe o tipo boolean diferente de C que o resultado seria 0 ou 1.


```

public class MainIfElse {

	public static void main(String[] args) {

		if (true){
			System.out.println("Existe o tipo True");
		}

		Integer teste = new Integer ((int) Math.random());

		if (teste > 10){
			System.out.println("Maior que 10");
		}else {
			System.out.println("Menor que 10");
		}
	}
}

```

----

## Condição switch case

A estrutura condicional Switch/Case é utilizada quando se tem vários casos de comparação
com poucas ações a serem executadas em cada caso:

```


import java.util.Scanner;

public class MainSwitchCaseJava {

	public static void main(String[] args) {

		Scanner s = new Scanner(System.in);

		Integer x = s.nextInt();

		switch (x) {
		case 1:
			System.out.println("O número 1 foi lido");
			break;
		default:
			System.out.println("Outro número foi lido");
			break;
		}

		String diaSemana = s.next();		
		String tipoDoDia;

	    switch (diaSemana) {
	         case "Segunda-Feira": tipoDoDia = "Início da Semana";
	             break;
	         case "Terça-Feira":
	         case "Quarta-Feira":
	         case "Quinta-Feira":
	        	 tipoDoDia = "Meio a semana";
	             break;
	         case "Sexta-Feira":
	        	 tipoDoDia = "Fim da Sema";
	             break;
	         case "Sábado":
	         case "Domingo":
	        	 tipoDoDia = "Acabou!";
	             break;
	         default:
	             throw new IllegalArgumentException("Dia da semana inválido");
	     }

	    System.out.println(tipoDoDia);

		// O Switch não funciona para String em versóes abaixo de Java 7

	    s.close();
	}
}

```


----

## Inline Contidion

São um tipo de condição que utiliza um operador ternário para realizar ações com base no resultado de uma operação.
Normalmente é utilizado para realizar atribuições mediante condição.
```

public static void main(String[] args) {

		Scanner s = new Scanner(System.in);

		int a;

		int i = s.nextInt();

		if (i == 0)
		{
		    a = 10;
		}
		else
		{
		    a = 5;
		}

		a = (i == 0) ? 10:5;

		s.close();
	}

```


----

## Estruturas de Repetição

As estruturas de Repetição são utilizadas para repetir a execução de determinadas ações se baseando em uma condição específica.


----

## Estrutura FOR

```

public class MainFor {

	public static void main(String[] args) {

		for(int i = 0 ; i < 10; i++){
			//Executa este bloco de código 10 vezes
			System.out.println("Você está no indicia "+ i);
		}
	}
}
```

----

## Estrutura While

Assim como o for, o while se baseai em uma condição. Porém a estrutura for possui um controle
do índice que ele está trabalhando, já no while o programador terá que fazer este trabalho.

```

public class MainWhile {

	public static void main(String[] args) {
		Scanner s = new Scanner(System.in);

		System.out.println("Digite um valor menor que zero");
		Integer num = s.nextInt();

		while (num > 0) {
			System.out.println("Digite um valor menor que zero");
			num = s.nextInt();
		}

		System.out.println("Obrigado, até mais!");
		s.close();

	}
}
```

----

## Estrutura do While

A diferença entre o 'while' e o 'do/while' é que no 'while' temos uma pré-condição para o código executar,
já no 'do/while' existe uma pós-condição para que o bloco continue sendo executado. Ou seja,
no 'do/while' o código sempre irá executar pelo menos uma vêz;


```

public class MainDoWhile {

	public static void main(String[] args) {
		Scanner s = new Scanner(System.in);

		Integer num;

		do {
			System.out.println("Digite um valor menor que zero");
			num = s.nextInt();
		}while (num > 0);

		System.out.println("Obrigado, até mais!");
		s.close();

	}
}

```


----


## Vetoresou Array

Vetores é utilizado quando existe a necessidade de se trabalhar com um conjunto de variáveis que está no mesmo conceito,
como exemplo seria um conjunto de 5 idades:

```
public class VetorSimples {

	public static void main(String[] args) {
		int idade1,idade2,idade3,idade4,idade5; //Declaração sem vetor

		Scanner s = new Scanner(System.in);

		int[] idades = new int [5];

		for (int i = 0 ; i < 5; i++){
			//Lendo valores para o vetor
			idades[i] = s.nextInt();
		}


		for (int i = 0 ; i < 5; i++){
			//Imprindo elementos do vetor
			System.out.println(idades[i]);
		}

		s.close();
	}
}

```

[Material Complementar](https://www.caelum.com.br/apostila-java-orientacao-objetos/um-pouco-de-arrays/#5-1-o-problema)


----


## Vetores  ou Array

Em Java é possível criar vetores de objetos, porém quando criamos uma array de alguma classe, ela possui apenas referências. O objeto, como sempre, está na memória principal e, no vetor, só ficam guardadas as referências (endereços).

```
Pessoa[] pessoas;
pessoas = new Pessoa[5];

```
Note:

Quantas pessoas foram criadas aqui? Na verdade, nenhuma. Foram criados 5 espaços que você pode utilizar para guardar uma referência a uma Pessoa. Por enquanto, eles se referenciam para lugar nenhum (null).

----

## Exemplo de vetor

```

## Exemplo Vetor de Objetos


public class VetorDeObjetos {

	public static void main(String[] args) {

		Pessoa [] pessoas = new Pessoa[5];


		System.out.println("Antes de Adicionar objetos --------------------------------------------------------------\n");
		// O que há no vetor? Apenas referências
		for (int i = 0 ; i < 5 ; i++){
			System.out.println(pessoas[i]);
		}

		System.out.println("Depois de Adicionar objetos --------------------------------------------------------------"\n);

		//Inserindo objetos
		for (int i = 0 ; i < 5 ; i++){
			pessoas[i] = new Pessoa(i*5, "Pessoa"+i);
		}

		// O que há no vetor? Refências a objetos existentes
		for (int i = 0 ; i < 5 ; i++){
			System.out.println(pessoas[i]);
		}

	}
}

```

----


## Listas

A linguagem Java ainda fornece algumas APIs que permitem armazenar objetos, uma delas
é a interface[List](https://docs.oracle.com/javase/7/docs/api/java/util/List.html), que pode ser implementada por uma séria de Classes:

<div style="text-align: left">

* [ArrayList](https://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html)
* [AbstractList](https://docs.oracle.com/javase/7/docs/api/java/util/AbstractList.html)
* [AbstractSequentialList](https://docs.oracle.com/javase/7/docs/api/java/util/AbstractSequentialList.html)
* [CopyOnWriteArrayList](https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/CopyOnWriteArrayList.html)
* [AttributeList](https://docs.oracle.com/javase/7/docs/api/javax/management/AttributeList.html)
* [LinkedList](https://docs.oracle.com/javase/7/docs/api/java/util/LinkedList.html)
* [RoleList](https://docs.oracle.com/javase/7/docs/api/javax/management/relation/RoleList.html)
* [RoleUnresolvedList](https://docs.oracle.com/javase/7/docs/api/javax/management/relation/RoleUnresolvedList.html)
* [Stack](https://docs.oracle.com/javase/7/docs/api/javax/management/relation/RoleUnresolvedList.html)
* [Vector](https://docs.oracle.com/javase/7/docs/api/java/util/Vector.html)

</div>

----


## Listas

A Interface [List](https://docs.oracle.com/javase/7/docs/api/java/util/List.html) fornece uma séria de métodos que
facilitam o trabalho de quem está utilizando. Como implementação de exemplo, utilizaremos o [ArrayList](https://docs.oracle.com/javase/7/docs/api/java/util/ArrayList.html).

```
public class MainListas {

	public static void main(String[] args) {

		ArrayList<Pessoa> pessoas = new ArrayList<>();

		//Inserindo objetos (Não é necessário utilizar o índice)
		for (int i = 0 ; i < 50 ; i++){
			pessoas.add(new Pessoa(i*5, "Pessoa"+i));
		}

		//Buscando Objetos pelo índice
		System.out.println(pessoas.get(2));

		//Removendo Objetos pelo índice
		System.out.println(pessoas.remove(3));

		System.out.println(pessoas.get(3));


	}
}

```


----

## Estrutura For Each

Quando utilizamos vetores ou listas e não necessitamos do índice que estamos percorrendo o vetor, podemos
utilizar uma estrutura de repetição muito interessante, o for each, que irá percorrer todo o vetor retornando os elementos
na ordem que estão inseridos.

```
import java.util.ArrayList;

import br.edu.unipac.exemplos.vetores.Pessoa;

public class MainForEach {

	public static void main(String[] args) {

		ArrayList<Pessoa> pessoasList = new ArrayList<>();

		//Inserindo objetos (Não é necessário utilizar o índice)
		for (int i = 0 ; i < 10 ; i++){
			pessoasList.add(new Pessoa(i*5, "PessoaList"+i));
		}

		// Utilizando o foreach para acessar elementos
		for (Pessoa pessoa : pessoasList){
			System.out.println(pessoa);
		}

		System.out.println("\n--\n");


		Pessoa [] pessoasVetor = new Pessoa[5];

		// Adicionando elementos no vetor (é necessário utilizar o índice
		for (int i = 0 ; i < 5 ; i++){
			pessoasVetor[i] = new Pessoa(i*5, "PessoaVetor"+i);
		}

		// Utilizando o foreach para acessar elementos
		for (Pessoa pessoa : pessoasVetor){
			System.out.println(pessoa);
		}
	}
}
```

----


## Comentário

No Java existem dois tipos de comentário:

```
public class OlaUnipac {
    // Comentário em Linha
    public static void main(String[] args) {
        /*
        Comentário em bloco
        */
        System.out.println("OlaUnipac");
    }

}

```

----

## Estrutura da Classe: Métodos

Um objeto pode executar as ações, essas ações possíveis são definidas em seus métodos.

```
public class Unipac {

    String nome;
    String endereco;

    public String retornaNome () {
      return nome;
    }

    public String retornaEndereco () {
      return endereco;
    }
}

```

----

## Estrutura da Classe: Declaração de Variáveis

As variáveis no java podem ser locais, ou seja, são declaradas no bloco em que são usadas.
Ou ainda, variáveis de instância, que são declaradas nas classes do bloco.

----

## Declaração de Variáveis - Locais

```
public class Calculadora {

    public int somaDois (int numero) {
      int dois = 2;
      int soma = dois + numero;
      return soma;
    } // Isto é apenas um exemplo

}

```

----

## Declaração de Variáveis - Instância

```
public class Calculadora {
    int dois = 2;

    public int somaDois (int numero) {

      int soma = dois + numero;
      return soma;
    }

    public int diminuiDois (int numero) {

      int soma =  numero - dois;
      return soma;
    }
}

```

----


## Tipos

Java é uma linguagem fortemente tipada, sendo assim, é necessário informar o
tipo de uma variável em sua declaração, e o mesmo nunca poderá ser alterado.

[Material Complementar](https://www.youtube.com/watch?v=JEAQeT7YGs4)

----


## Tipos primitivos

Os tipos primitivos em Java são aqueles que guardam o valor real das variáveis.
São tipos primitivos em JAVA: byte, short, int, long, float, double, char.


[Fonte: Oracle](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/datatypes.html)

Note:
Um inteiro literal é de tipo longo se termina com a letra L ou l; Caso contrário, é do tipo int.
// O número 26, em decimal
Int decVal = 26;
// O número 26, em hexadecimal
Int hexVal = 0x1a;
// O número 26, em binário
Int binVal = 0b11010;
double d1 = 123.4;
// Mesmo valor utilizando ponto flutuante ou notação científica
double d2 = 1.234e2;
float f1  = 123.4f;

----  ----

# 3. Exercício prático (ex1)

A forma mais simples de aprender a utilizar classes é criando cenários da vida real.

----

## Classe de um Computador

Crie um cenário pensando no computador:
* Liste 10 propriedades
* Liste 2 componentes Internos
* Liste 2 ações para o computador
* Liste 1 ações para cada componente

----

## Exercício

Tente passar tudo que foi criado para a linguagem Java.

----  ----

# 4. Entrada e Saída

A linguagem Java possui diversos tipos de entrada e saída de dados, os principais
são pela entrada padrão e por argumentos.

----

## Saída de dados

A saída de dados padrão do Java é o terminal. Para utilizá-la é necessário utilzar
o seguinte código:

```
 System.out.println("OlaUnipac");
 ou
 System.out.printf("A soma é %d%n", soma);
```

----

## Caracteres especiais

* \n Nova linha
* \t Tab na horizontal
* \r Retorna o cursor
* \\\\ Barra
* \" Aspas

----

## Entrada de dados - Scanner

A classe Scanner realiza a leitura de dados da entrada padrão (teclado).

```
import java.util.Scanner;

public class Somador {
  public static void main(String[] args){

    Scanner input = new Scanner(System.in);
    int numero1;
    int numero2;
    int soma;

    System.out.print("Digite o número 1 ");
    numero1 = input.nextInt();
    System.out.print("Digite o número 2 ");
    numero2 = input.nextInt();
    soma = numero1 + numero2;
    System.out.printf("A soma é %d%n", soma);
  }
}
```

----

## Entrada de dados - Args

O args que está no método main é utilizado para a entrada de dados:

```
public class Echo {
    public static void main (String[] args) {
        for (String s: args) {
            System.out.println(s);
        }
    }
}
```

```
javac Echo.java
```

```
java Echo Drink Hot Java

```

```
java Echo "Drink Hot Java"

```

----  ----

# 5. Métodos

Os métodos são conhecidos como funções, ações de execuções ou procedimentos, sendo responsáveis por ajudar no design do sistema (separação por blocos), e na reutilização de software, podendo ser aproveitados métodos já existentes para a construção de novos sistemas [DevMedia](http://www.devmedia.com.br/trabalhando-com-metodos-em-java/25917).

Note:

[Material Complementar](https://youtu.be/wNaoX6VOj54)

----

## Estrutura  

<img src="img/metodos.jpg" width="500">


----


## Nomenclatura

A primeira letra deve ser minúscula, e então as regras Camel Case normais devem ser usadas. Além disso, os nomes normalmente devem ser pares de verbos e substantivos.

----

## Local de criação

Os métodos devem ser criados dentro da classe.

----

## Sobrecarga

Em uma mesma classe pode haver vários métodos com o mesmo nome, contanto que possuam listas de argumentos distintas. Os argumentos podem variar em número, tipo e ordem de declaração.

----

## Exemplo de Sobrecarga

```

class MetodoSobrecarregado{

	public void testaMetodosSobrecarregados()
	{
		System.out.printf("Salário em número inteiro = %d\n", salario(700));
		System.out.printf("Salário em número double = %f\n", salario(7.500));
	}

	public int salario(int valorInt)
	{
		System.out.printf("\n Salário com argumento de inteiro = %d\n", valorInt);
		return valorInt * valorInt;
	}

	public double salario( double valorDouble)
	{
		System.out.printf("\n Salário chamado com argumento de double = %f\n", valorDouble);
		return valorDouble * valorDouble;
	}
}

public class Test_Metodos_Sobrecarregados {

	public static void main(String[] args) {

		MetodoSobrecarregado testaM = new MetodoSobrecarregado();
		testaM.testaMetodosSobrecarregados();
	}
}
```

----

## Retorno de um método

No Java um método deve informar o tipo de dados que retorna, ou informar que não retorna nada.

----

## Método sem retorno


```

class Metodo2{
	public void escrever()
	{
		System.out.println("Método sem Retorno - VOID ");
	}
}

public class Metodos_Sem_Retorno {

	public static void main(String[] args) {

		Metodo2 m = new Metodo2();
		m.escrever();
	}
}

```

----

## Método com retorno


```
class Metodo3{

	String nome = "João Silva";

	public String retornaNome()
	{
		return nome;
	}
}

public class Metodo_Com_Retorno {

	public static void main(String[] args) {

		Metodo3 m3 = new Metodo3();
		System.out.println(m3.retornaNome());

	}

}


```

----

## Método Static

Os métodos static ou métodos da classe são funções que não dependem de nenhuma
variável de instância, quando invocados executam uma função sem a dependência do
conteúdo de um objeto ou a execução da instância de uma classe, conseguindo
chamar direto qualquer método da classe e também manipulando alguns campos da classe.

----

## Exemplo de Método Static

```
class Soma{

	public static int resultado(int num1, int num2){
		return (num1 + num2);
	}
}

public class TestaSomaEstatica {

	public static void main(String[] args) {

		System.out.println(Soma.resultado(10,50));
	}
}

```

----  ----

# Modificadores de Acesso

Os modificadores de acesso são padrões de visibilidade de acessos às classes,
atributos e métodos. Esses modificadores são palavras-chave reservadas pelo Java,
ou seja, palavras reservadas não podem ser usadas como nome de métodos, classes ou atributos.
( public , protected , private, default )

----

## Modificador Default

Uma classe com acesso padrão não possui modificador declarado. Isto permite que você tenha
acesso ao nível de pacote, ou seja, uma classe com acesso padrão pode ser vista somente pelas
classes dentro do mesmo pacote.

----

## Exemplo de Modificador default

```

package bebidas;
class Bebida { }

package br.unipac; // Erro
import bebidas.Bebida;
class Cha extends Bebida { }

package bebidas;
import bebidas.Bebida;
class Cerveja extends Bebida { }

```

----

## Modificador Public

Uma declaração com o modificador public dá á todas as classes de todos os pacotes acesso à  este recurso
(classe ou método). Mas, ainda é necessário utilizar o import



----

## Exemplo de Modificador public

```

package bebidas;
public class Bebida { }

package br.unipac;
import bebidas.Bebida;
class Cha extends Bebida { }

```

----


## Modificador Private

Uma declaração marcada como privada não podem ser acessadas por códigos em qualquer classe
diferente da Classe de origem. Este modificador pode ser aplicado a métodos e e atributos de classe

----

## Exemplo de Modificador private


```

package br.edu.unipac.exercicios.ex1;

public class Memoria {

	private String modelo;
	private Integer capacidadeEmGb;

	public String getModelo() {
		return modelo;
	}
	public void setModelo(String modelo) {
		this.modelo = modelo;
	}

}

```

----

## Modificador Protected


Os níveis de controle de acesso protected e default são semelhantes, mas com uma
diferença crítica. Um membro default só pode ser acessado se a classe que está acessando
pertence ao mesmo pacote, enquanto um membro protected pode ser acessado
por meio da herança) por uma subclasse, mesmo que a subclasse esteja em um pacote diferente.


----

## Exemplo de Modificador protected


```

package bebidas;
protected class Bebida { }

package br.unipac;
import bebidas.Bebida;
class Cha extends Bebida { }

package bebidas;
import bebidas.Bebida;
class Cerveja extends Bebida { }

```


----  ----

# Propriedades e Relacionamentos

Neste capítulo vamos definir algumas propriedades e relacionamentos que podem ocorrer entre as classes.

[Material Complementar](https://youtu.be/GLHbxDU9iBA)

----

## Associação

Uma associação consiste em um relacionamento entre objetos destas classes, ou seja, elas estão conectadas por um aspecto.

```

public class Cliente {

	String nome;

}

public class Pedido {

	String descricao;
	Cliente cliente;
}

public class MainAssociacao {

	public static void main(String[] args) {

		Cliente cliente1 = new Cliente("Cliente1");

		Pedido pedido1 = new Pedido("Pedido-1", cliente1);

		Pedido pedido2 = new Pedido("Pedido-2", cliente1);

		System.out.println(pedido1);

		System.out.println(pedido2);
	}
}

```

----

## Agregação

É uma associação unidirecional entre objetos. Esta associação pode ser representada
pelo termo 'tem um' ou 'tem vários'. Mas, os dois objetos envolvidos podem 'sobreviver'
individualmente, ou seja, seus ciclos de vida não são relacionados.

[Material Complementar](https://youtu.be/ERdvijGtrq0)


----

## Agregação

```

----------------

public class Aluno {

	String nome;

}

----------------

import java.util.Arrays;

public class Turma {

	Aluno [] alunos;

}

----------------

public class MainAgregacao {

	public static void main(String[] args) {

		Aluno aluno1 = new Aluno("Aluno1");
		Aluno aluno2 = new Aluno("Aluno2");
		Aluno aluno3 = new Aluno("Aluno1");

		Aluno  alunos [] = new Aluno[]{aluno1,aluno2,aluno3};

		Turma turma = new Turma(alunos);

		// Turma é uma agregação de alunos, mas alunos existem sem turma
		System.out.println(turma);
	}
 }


```

----

## Composição

Composição é uma forma restrita de Agregação na qual duas entidades são altamente dependentes. Na composição, ambas as entidades são dependentes umas das outras. Quando há uma composição entre duas entidades, o objeto composto não pode existir sem a outra entidade.


```

import java.util.Arrays;

public class Cardapio {

	ItemCardapio [] item;

  //Adicionar Construtor e toString

}

----------------

public class ItemCardapio {

	String descricao;

  //Adicionar Construtor e toString

}

----------------

public class MainComposicao {

	public static void main(String[] args) {

		ItemCardapio item1 = new ItemCardapio("Arroz");
		ItemCardapio item2 = new ItemCardapio("Feijão");

		ItemCardapio[] itens = new ItemCardapio[] {item1,item2};

		Cardapio cardapio = new Cardapio(itens);

		System.out.println(cardapio);

	}
}
```

----


## Agregação vs Composição

Dependência:
* Agregação implica um relacionamento em que o filho pode existir independentemente do pai. Por exemplo, Banco e Empregado.
* Composição implica uma relação onde o objeto filho não pode existir independente do pai. Exemplo: humano e coração.
* Tipo de Relacionamento: A relação de agregação é 'tem-um' e a composição é 'parte-de'.
* Tipo de associação: A composição é uma associação forte, enquanto a agregação é uma associação fraca.

----


## Generalização

A generalização é um tipo de relação onde existe um elemento mais geral e outro mais específico. O elemento
específico contém tudo que o geral tem mais as suas especifidades.

```
public class Aluno extends Pessoa {

	String matricula;

  //Adicionar Construtor e toString

}

----------------

public class Docente extends Pessoa{

	String carteiraDeTrabalho;

  //Adicionar Construtor e toString

}

----------------

public class Pessoa {

	String nome;

  //Adicionar Construtor e toString



}

----------------

public class MainGeneralizacao {


	public static void main(String[] args) {

		Aluno aluno = new Aluno("Aluno-1", "1111111");

		System.out.println(aluno);

		Docente docente = new Docente("Docente-1", "22222222");

		System.out.println(docente);

		Pessoa p = aluno;

		System.out.println("Aluno: "+ p);

		p = docente;

		System.out.println("Docente: "+ p);

    p = new Pessoa("Pessoa");
	}

}

```

----


## Classe Abstrata

Quando o elemento mais genérico é apenas uma definição, ou seja, não podemos criar um objeto dele, utilizamos
as classes abstratas. Estas classes podem apenas ser herdadas e não podem gerar novas instâncias.


```
public class MainAbstracao {



	public static void main(String[] args) {


		ContaCorrente cc = new ContaCorrente();
		ContaPoupanca cp = new ContaPoupanca();

		System.out.println("Classe: "+ cc.getClass().getName());
		System.out.println("Classe pai: "+ cc.getClass().getSuperclass().getName());

		System.out.println("Classe: "+ cp.getClass().getName());
		System.out.println("Classe pai: "+ cp.getClass().getSuperclass().getName());

		//Para criar uma instância de conta seria necessário implementar o método abstrato

		Conta c = new Conta() {

			@Override
			public Double calculaJuros() {
				return null;
			}
		};
	}
}


```

[Material Complementar](https://www.caelum.com.br/apostila-java-orientacao-objetos/classes-abstratas/#9-7-desafios)

----


## Interface

As interfaces representam um contrato, ou seja, uma garantia que determinados métodos serão implementados por uma classe.


```
public interface Calculador {

	Integer calucla(Integer n1, Integer n2);
}

----------------

public class CalculadoraSoma implements Calculador{

	@Override
	public Integer calucla(Integer n1, Integer n2) {
		return n1 + n2;
	}

}

----------------

public class CalculadoraSubtracao implements Calculador{

	@Override
	public Integer calucla(Integer n1, Integer n2) {
		return n1 - n2;
	}


}

----------------

public class MainInterface {

	public static void main(String[] args) {
		Scanner s = new Scanner(System.in);

		System.out.println("Digite a operação");
		String op = s.next().trim();

		System.out.println("Digite n1\n");
		Integer n1 = s.nextInt();

		System.out.println("Digite n2\n");
		Integer n2 = s.nextInt();

		switch (op) {
		case "+":
			System.out.println(new CalculadoraSoma().calucla(n1, n2));
			break;
		case "-":
			System.out.println(new CalculadoraSubtracao().calucla(n1, n2));
			break;
		default:
			System.out.println("Operação não conhecida");
			break;
		}

		s.close();
	}
}

```
[Material Complementar](https://www.caelum.com.br/apostila-java-orientacao-objetos/interfaces/#10-1-aumentando-nosso-exemplo)


----  ----


# Exceptions

- Como podemos tratar situações de erro em um programa?
- Como avisar aquele que chamou o método de que ele não conseguiu fazer aquilo que deveria?
- Como avisar que o parâmetro passado não está correto?

Para isto utilizamos as exceptions.


----

## Exceptions

Um método possui uma definição de como deverá ser seu funcionamento, qualquer estado
não esperado ele lançará uma exceção que poderá ser de dois tipos, as checked e unchecked.

As exceções do tipo checked são de tratamento obrigatório, já as do tipo unchecked é de tratamento opcional.

----

## Exceptions - Exemplo (NullPointerException)

Acesso a um recurso não existente (Unchecked).

```
public class Pessoa {
  String nome;
}

public class MainNullPointer {

	public static void main(String[] args) {

		Pessoa p = null;

		System.out.println(p.nome);
	}
}

```

[Documentação](https://docs.oracle.com/javase/7/docs/api/java/lang/NullPointerException.html)

----

## Exceptions - Exemplo (ArrayIndexOutOfBoundsException)

Acesso a uma posição não existente (Unchecked).

```

public class MainArrayIndexException {

	public static void main(String[] args) {
		int[] array = new int[10];
		for (int i = 0; i <= 15; i++) {
			array[i] = i;
			System.out.println(i);
		}
		System.out.println("fim do metodo2");
	}

}

```

[Documentação](https://docs.oracle.com/javase/7/docs/api/java/lang/ArrayIndexOutOfBoundsException.html)

----

## Exception Customizada


Criando uma exceção para uma situação específica (Checked).

```

public class MainExceptionCustomizada {

	public static void main(String[] args) {
		try {
			olaMundo();
		} catch (MinhaException e) {
			e.printStackTrace();
		}
	}

	public static void olaMundo () throws MinhaException{
		throw new MinhaException();
	}
}


```

----

## Tratamento de Exceções

Já aprendemos a criar as exceções, e como tratá-las?

O tratamento é feito utilizando os blocos try/catch

----

## Tratamento de Exceções

```
public class MainExceptionCustomizada {

	public static void main(String[] args) {
		try {
			olaMundo();
		} catch (MinhaException e) {
			e.printStackTrace();
		}
	}

	public static void olaMundo () throws MinhaException{
		throw new MinhaException();
	}
}


```

----

## Bloco Finally

O bloco finally é um bloco que sempre será executado. O mesmo poderá ser utilizado
para ações como fechar stream de dados, conexões, entre outros.

```

public class MainExceptionCustomizada {

	public static void main(String[] args) {
		try {
			olaMundo();
		} catch (MinhaException e) {
			e.printStackTrace();
		}finally {
			System.out.println("Sempre irá ser executado");
		}
	}

	public static void olaMundo () throws MinhaException{
		throw new MinhaException();
	}
}

```

----  ----

# Arquivos

Quando estamos criando um software, muitas vezes temos que lidar com manipulação de arquivos, seja para ler dados de configuração, armazenar dados ou manipular arquivos no sistema de arquivos. A linguagem Java provê APIs de manipulação de arquivos, são elas Java.io, Java.nio e “Java.nio.2”.


----

## Java. (io x nio x nio.2)

É importante entender que uma API não veio para substituir a outra, mas sim para complementar.


----

## Java.io

Fornece entrada e saída do sistema através de fluxos de dados, serialização e sistema de arquivos. É a API mais básica para leitura e escrita de arquivos, suas operações são bloqueantes e são orientadas a streams,


----


## Java.nio

Fornece uma API orientada a buffer, permitindo operações de entreada e saída não bloqueantes, aumentando o desempenho da aplicação.


----

## Java.io - File

Um [File](https://docs.oracle.com/javase/7/docs/api/java/io/File.html) consiste em representação abstrata de caminho de arquivos e diretórios, ou seja, uma visão abstrata, independente do sistema de arquivo e sistema operacional.


----


## Java.io - File - Construtor

```
File(File parent, String child)
//Cria uma instância a partir de um 'pai' abstrado
File(String pathname)
//Cria uma instância de um File, convertêndo o caminho abstrado no caminho do sistema de arquivos
File(URI uri)
//Cria uma instância de um File a partir de uma URI

```


----


## Java.io - File - Funções

```

import java.io.File;

public class FuncoesFile {

	public static final String BASE_PATH = "/tmp";
	public static final String ARQUIVO_TESTE = "file-teste.txt";

	public static void main(String[] args) {


	      File f = new File(BASE_PATH + File.separator + "file.tmp");

	      System.out.println("Path absoluto: " + f.getAbsolutePath());
	      System.out.println("Arquivo existe: " + f.exists());
	      System.out.println("Pode ser lido: " + f.canRead());
	      System.out.println("Pode ser escrito: " + f.canWrite());
	      System.out.println("Pode ser executado: " + f.canExecute());
	      System.out.println("É arquivo: " + f.isFile());
	      System.out.println("É diretorio: " + f.isDirectory());



	      File dir = new File(BASE_PATH + File.separator + "diretorio");

	      if (dir.isDirectory()) {

	    	  for (File dirFile : dir.listFiles()) {
	    		  System.out.println(dirFile.getAbsolutePath());
	    	  }
	      }


	}
}


```

----

## Arquivo - Escrita


A manipulação de arquivos pode ser feita basicamente com as operações de leitura, escrita, criação e deleção. Mas,
existem várias formas de executar estas ações utilizando a linguagem Java.


----

## Arquivo - File Writer


```

package br.com.unipac.file;

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileOutputStream;
import java.io.FileWriter;
import java.io.IOException;

import com.thedeanda.lorem.Lorem;
import com.thedeanda.lorem.LoremIpsum;

public class EscritaArquivo {

	public static final String BASE_PATH = "/tmp/diretorio";
	public static final String ARQUIVO_TESTE = "file-teste.txt";

	public static void main(String[] args) {
		escritaComFileWriter();
	}


	public static void escritaComFileWriter() {

		Lorem lorem = LoremIpsum.getInstance();

		File f = new File(BASE_PATH + File.separator + lorem.getWords(1));

		try {
			if (f.createNewFile()) {
				FileWriter writer = new FileWriter(f);
				writer.write(lorem.getParagraphs(1, 50));
			    writer.flush();
			    writer.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}

	}

}


```

----

## Arquivo - Buffered Writer

```

package br.com.unipac.file;

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileOutputStream;
import java.io.FileWriter;
import java.io.IOException;

import com.thedeanda.lorem.Lorem;
import com.thedeanda.lorem.LoremIpsum;

public class EscritaArquivo {

	public static final String BASE_PATH = "/tmp/diretorio";
	public static final String ARQUIVO_TESTE = "file-teste.txt";

	public static void main(String[] args) {
		escritaComBufferedWriter();
	}

	public static void escritaComBufferedWriter() {

		Lorem lorem = LoremIpsum.getInstance();

		File f = new File(BASE_PATH + File.separator + lorem.getWords(1));

		try {
			if (f.createNewFile()) {

				BufferedWriter buffer = new BufferedWriter(new FileWriter(f));
				buffer.write(lorem.getParagraphs(1, 50));
			    buffer.flush();
			    buffer.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}

	}

}


```

----

## Arquivo - Buffered Writer

```

package br.com.unipac.file;

import java.io.BufferedWriter;
import java.io.File;
import java.io.FileOutputStream;
import java.io.FileWriter;
import java.io.IOException;

import com.thedeanda.lorem.Lorem;
import com.thedeanda.lorem.LoremIpsum;

public class EscritaArquivo {

	public static final String BASE_PATH = "/tmp/diretorio";
	public static final String ARQUIVO_TESTE = "file-teste.txt";

	public static void main(String[] args) {
		escritaComFileOutPutStream();
	}

	public static void escritaComFileOutPutStream() {

		Lorem lorem = LoremIpsum.getInstance();

		File f = new File(BASE_PATH + File.separator + lorem.getWords(1));
		try {

			if (f.createNewFile()) {
				FileOutputStream fous = new FileOutputStream(f);
				fous.write(lorem.getParagraphs(1, 50).getBytes());
				fous.flush();
				fous.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}

	}
}


```

----

## Arquivo Leitura - File Reader

```

package br.com.unipac.file;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileReader;
import java.io.IOException;

public class LeituraArquivo {

	public static final String BASE_PATH = "/tmp";

	public static void main(String[] args) {

		File dir = new File(BASE_PATH + File.separator + "diretorio");

	      if (dir.isDirectory()) {

	    	  for (File dirFile : dir.listFiles()) {
	    		  leituraComFileReader(dirFile);
	    	  }
	      }
	}


	public static void leituraComFileReader(File f) {

		try {
			if (f != null && f.exists() && f.canRead()) {
				System.out.println("(File Reader) - Realizando leitura do arquivo " + f.getAbsolutePath());
				FileReader reader = new FileReader(f);
				char buffer [] = new char [(int) f.length()];
				reader.read(buffer);
				System.out.println(buffer);
				reader.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}

	}


}


```

----

## Arquivo Leitura - Buffered Reader

```

package br.com.unipac.file;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileReader;
import java.io.IOException;

public class LeituraArquivo {

	public static final String BASE_PATH = "/tmp";

	public static void main(String[] args) {

		File dir = new File(BASE_PATH + File.separator + "diretorio");

	      if (dir.isDirectory()) {

	    	  for (File dirFile : dir.listFiles()) {

	    		  leituraComBufferedReader(dirFile);
	    		  leituraComBufferedReaderJava8(dirFile);
	    	  }
	      }
	}





	public static void leituraComBufferedReader(File f) {

		try {
			if (f != null && f.exists() && f.canRead()) {
				System.out.println("(Buffered Reader) - Realizando leitura do arquivo " + f.getAbsolutePath());
				FileReader reader = new FileReader(f);
				BufferedReader buffereader = new BufferedReader(reader);
				String linha;

				while ((linha = buffereader.readLine()) != null) {
					System.out.println(linha);
				}

				buffereader.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}


	public static void leituraComBufferedReaderJava8(File f) {

		try {
			if (f != null && f.exists() && f.canRead()) {
				System.out.println("(Buffered Reader Java 8) - Realizando leitura do arquivo " + f.getAbsolutePath());
				FileReader reader = new FileReader(f);
				BufferedReader buffereader = new BufferedReader(reader);

				buffereader.lines().
				map(String::toUpperCase).
				forEach(System.out::println);
				buffereader.close();

			}
		} catch (IOException e) {
			e.printStackTrace();
		}
	}


}


```

----

## Arquivo Leitura - InputStream

```

package br.com.unipac.file;

import java.io.BufferedReader;
import java.io.File;
import java.io.FileInputStream;
import java.io.FileReader;
import java.io.IOException;

public class LeituraArquivo {

	public static final String BASE_PATH = "/tmp";

	public static void main(String[] args) {

		File dir = new File(BASE_PATH + File.separator + "diretorio");

	      if (dir.isDirectory()) {

	    	  for (File dirFile : dir.listFiles()) {
	    		  leituraComFileReader(dirFile);
	    		  leituraComBufferedReader(dirFile);
	    		  leituraComFileInputStream(dirFile);
	    		  leituraComBufferedReaderJava8(dirFile);
	    	  }
	      }
	}

	public static void leituraComFileInputStream(File f) {

		try {
			if (f != null && f.exists() && f.canRead()) {
				System.out.println("(File Input Stream) - Realizando leitura do arquivo " + f.getAbsolutePath());

				FileInputStream finput = new FileInputStream(f);

				byte[] buffer = new byte [(int) f.length()];
				finput.read(buffer);
				System.out.println(new String(buffer));
				finput.close();
			}
		} catch (IOException e) {
			e.printStackTrace();
		}

	}

}


```

----


## Java io vs nio

![](img/nio-vs-io-1.png)


Fonte: [DZone](https://dzone.com/articles/java-nio-vs-io)


----


## Java io vs nio

![](img/nio-vs-io-1.png)


Fonte: [DZone](https://dzone.com/articles/java-nio-vs-io)


----

## Funções Complementares - Copy

```

package br.com.unipac.file;

import java.io.File;
import java.io.FileWriter;
import java.io.IOException;
import java.nio.file.CopyOption;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.nio.file.StandardCopyOption;

import com.thedeanda.lorem.Lorem;
import com.thedeanda.lorem.LoremIpsum;

public final class CopiaFile {

	  public static final String BASE_PATH = "/tmp/diretorio";

	  public static void main(String... aArgs) throws IOException {

      // Criação do Arquivo
		  Lorem lorem = LoremIpsum.getInstance();
    	  File f = new File(BASE_PATH + File.separator + lorem.getWords(1));

			try {
				if (f.createNewFile()) {
					FileWriter writer = new FileWriter(f);
					writer.write(lorem.getParagraphs(1, 50));
				    writer.flush();
				    writer.close();
				}
			} catch (IOException e) {
				e.printStackTrace();
			}

      //Copia do Arquivo
	    Path origem = Paths.get(f.getAbsolutePath());
	    Path destino = Paths.get(f.getAbsolutePath()+"2");

	    CopyOption[] options = new CopyOption[]{
	      StandardCopyOption.REPLACE_EXISTING,
	      StandardCopyOption.COPY_ATTRIBUTES
	    };
	    Files.copy(origem, destino, options);
	  }
	}

```

----

## Materiais Complementares - Copy

* [FileChannel](https://docs.oracle.com/javase/7/docs/api/java/nio/channels/FileChannel.html)

* [java.util.stream](https://docs.oracle.com/javase/8/docs/api/java/util/stream/package-summary.html)

* [Exemplos Oracle](https://docs.oracle.com/javase/7/docs/technotes/guides/io/example/)


----  ----

## Atividades

As atividades desenvolvidas no semestre poderão ser encontradas neste capítulo.


----

## Artigos

A sala deverá ser dividida em grupo de quatro pessoas para que sejam realizadas discussões
sobre os seguintes artigos:

[Apresentação dia 20/02/2018](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/papers/nosilverbullet.pdf)

[Apresentação dia 27/03/2018](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/papers/theroleofprogramingparadigm.pdf)

[Apresentação dia 15/05/2018](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/papers/whatispoo.pdf)

----

## Listas de Exercícios


[Lista - 1 - Introdução a POO](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/01-lista.pdf)

[Lista - 2 - Introdução a Java e Revisão](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/02-lista.pdf)

[Lista - 3 - Classes e Construtores](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/03-lista.pdf)

[Lista - 4 - Métodos](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/04-lista.pdf)

[Lista - 5 - Modificadores de Acesso](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/05-lista.pdf)

[Lista - 6 - Polimorfismo](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/06-lista.pdf)

[Lista - 7 - Sobrecarga e Sobreposição](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/07-lista.pdf)

[Lista - 8 - Listas, Exceptions, File e Date](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/listas/08-lista.pdf)

----

## Enade

[Enade 2014 - Prova](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/enade/2014/prova.pdf)/
[Enade 2014 - Gabarito](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/enade/2014/gabarito.pdf)/
[Enade 2014 - Respostas](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/enade/2014/respostas.pdf)

[Enade 2017 - Prova](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/enade/2017/prova.pdf)/
[Enade 2017 - Gabarito](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/enade/2017/gabarito.pdf)


----

## Poscomp

[Poscomp 2016 - Prova](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/poscomp/prova.pdf)

[Poscomp 2016 - Gabarito](https://diego91964.github.io/unipac/disciplinas/programacao-orientada-a-objetos/doc/poscomp/gabarito.pdf)

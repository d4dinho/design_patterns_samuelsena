# Padrões de Projeto
Neste projeto, eu explorei os três principais tipos de padrões de projeto: Criacionais, Estruturais e Comportamentais. Esses padrões são soluções já consolidadas para problemas recorrentes no design de software e ajudam a tornar o código mais organizado, reutilizável e fácil de manter.

# Criacionais
Os padrões de projeto criacionais tratam da criação de objetos de maneira flexível e eficiente, evitando que o código fique rigidamente acoplado a classes específicas. Eles abstraem o processo de instanciação, tornando-o mais independente das implementações concretas utilizadas.

Factory Method (Método de Fábrica)

O padrão Factory Method define uma interface para a criação de objetos, permitindo que as subclasses decidam qual classe concreta será instanciada. Assim, a responsabilidade de criar os objetos é delegada, tornando o código mais flexível e fácil de estender.

Problema:
Imagine que você está desenvolvendo um sistema de logística que trabalha com diferentes tipos de veículos — carros, bicicletas e caminhões. Em determinado ponto, você precisa criar instâncias desses veículos, mas não quer que o código dependa diretamente das classes concretas. Esse acoplamento rígido dificultaria alterações e a expansão do sistema no futuro.

Solução:
O Factory Method resolve essa situação ao definir um método de criação genérico, deixando que subclasses determinem qual objeto concreto será criado. Dessa forma, a lógica de criação fica encapsulada, promovendo maior flexibilidade, extensibilidade e desacoplamento.
Diagrama UML:
<img width="756" height="509" alt="image" src="https://github.com/user-attachments/assets/78007863-9def-4e9c-b3b8-eaf702dda463" />

imagem do site: https://refactoring.guru/pt-br/design-patterns/factory-method

Código de exemplo e com explicação (retirado do site: https://refactoring.guru/pt-br/design-patterns/factory-method/python/example):

<img width="804" height="262" alt="image" src="https://github.com/user-attachments/assets/20dbacb3-b456-4256-9ec0-2ec5afc14849" />

A classe Creator é uma classe abstrata que declara o método factory_method(), responsável por retornar um objeto do tipo Product. Ela também possui o método some_operation(), que demonstra como o criador utiliza o objeto retornado pelo factory_method(). O ponto importante é que a classe Creator não depende das classes concretas de produtos, o que mantém o código flexível, desacoplado e fácil de estender.

<img width="398" height="167" alt="image" src="https://github.com/user-attachments/assets/5fd6ed80-478f-4db9-a6cf-7ea6d05f4c9f" />

As classes ConcreteCreator1 e ConcreteCreator2 são subclasses concretas de Creator. Cada uma delas implementa o método factory_method(), retornando instâncias de produtos específicos — ConcreteProduct1 e ConcreteProduct2, respectivamente. Dessa forma, cada criador define qual produto concreto será instanciado.

<img width="344" height="114" alt="image" src="https://github.com/user-attachments/assets/b9b2e669-1c93-4629-9add-25359fc5400f" />

Product (Produto): É uma interface que declara o método operation(), que todos os produtos concretos devem implementar.

<img width="477" height="173" alt="image" src="https://github.com/user-attachments/assets/af706274-072b-48bc-a58a-4a27040748d3" />

ConcreteProduct1 e ConcreteProduct2: São implementações concretas da interface Product que fornecem diferentes implementações para o método operation().

<img width="683" height="248" alt="image" src="https://github.com/user-attachments/assets/5c63ee5e-b91a-492a-a2c9-1c5df298cc81" />

A função client_code() recebe um objeto do tipo Creator e demonstra como o código cliente pode operar utilizando criadores e produtos sem precisar conhecer suas classes concretas. Isso evidencia o desacoplamento proporcionado pelo padrão.

O bloco if __name__ == "__main__": é utilizado para verificar se o script está sendo executado diretamente, e não importado como módulo. Nesse caso, ele serve para exemplificar como o cliente pode trabalhar com diferentes criadores e produtos, mostrando o comportamento do sistema com várias implementações do Factory Method.

# Estruturais
Os padrões de projeto estruturais tratam da composição de classes e objetos para formar estruturas maiores, facilitando a interação entre seus componentes. Eles ajudam a garantir que mudanças internas em uma estrutura não impactem negativamente as partes que dependem dela.

Adapter (Adaptador)

O padrão Adapter converte a interface de uma classe em outra interface esperada pelo cliente. Isso permite que classes com interfaces incompatíveis trabalhem juntas, possibilitando a reutilização de código existente sem alterar sua implementação original.

Problema:
Imagine que você possui uma classe já existente cuja interface não corresponde ao formato esperado pelo cliente. Ajustar essa classe para atender à interface desejada pode ser inviável ou simplesmente indesejado, seja por restrições técnicas ou por questões de manutenção.

Solução:
O padrão Adapter resolve esse problema criando um adaptador capaz de traduzir a interface original para a interface esperada. Dessa forma, objetos com interfaces incompatíveis passam a se comunicar sem necessidade de alterar o código legado.

Diagrama da UML:

<img width="622" height="495" alt="image" src="https://github.com/user-attachments/assets/54c325e5-8549-4e83-aef7-b8fb6ed6c40f" />

imagem do site: https://refactoring.guru/pt-br/design-patterns/adapter

Código de exemplo e com explicação (retirado do site: https://refactoring.guru/pt-br/design-patterns/adapter/python/example):

<img width="495" height="173" alt="image" src="https://github.com/user-attachments/assets/4e012052-1ec9-4554-ae60-5fb574c74f15" />

Target (Alvo):
Define a interface específica do domínio que o código cliente espera utilizar. Inclui o método request(), que representa o comportamento padrão oferecido pelo alvo.

Adaptee (Adaptado):
Representa uma classe que possui um comportamento útil, porém exposto por meio de uma interface incompatível com o que o cliente espera. Ela fornece o método specific_request(), que encapsula esse comportamento específico do adaptado.

<img width="615" height="159" alt="image" src="https://github.com/user-attachments/assets/fac2df51-be0f-41d3-a7f0-44706811b4d8" />

Adapter (Adaptador):
Torna a interface do Adaptee compatível com a interface do Target por meio de herança múltipla. Ele implementa o método request() para traduzir e adaptar o comportamento do Adaptee, garantindo que o código cliente receba exatamente o formato de interação que espera.

client_code():
Aceita qualquer objeto que siga a interface Target, mostrando como o código cliente pode operar de forma independente das classes concretas. Isso permite trabalhar diretamente com objetos Target, mas também possibilita o uso de um Adaptee por meio do Adapter, sem modificar o cliente.

<img width="579" height="271" alt="image" src="https://github.com/user-attachments/assets/a0690172-4b99-48d0-85d0-614e710e195a" />

if name == "main":: Verifica se o script está sendo executado diretamente como um programa. No bloco, o cliente demonstra como ele pode trabalhar com objetos Target, Adaptee e Adapter.

# Comportamentais 
Os padrões de projeto comportamentais focam na interação entre objetos, definindo responsabilidades e a forma como eles se comunicam. Eles ajudam a estabelecer como os objetos colaboram para executar tarefas complexas dentro do sistema.

Strategy (Estratégia)

O padrão Strategy define uma família de algoritmos, encapsulando cada um deles e tornando-os intercambiáveis. Com isso, o algoritmo pode variar de forma independente do cliente que o utiliza, promovendo flexibilidade, manutenção mais simples e maior reutilização de código.

Problema:
Você precisa implementar diferentes algoritmos para realizar uma tarefa específica e deseja permitir que esses algoritmos possam ser escolhidos ou alterados sem modificar o código do cliente.

Solução:
O padrão Strategy resolve esse problema ao encapsular cada algoritmo em uma classe separada, permitindo que todos sejam intercambiáveis. Assim, o cliente pode selecionar dinamicamente qual algoritmo deseja utilizar, sem depender diretamente de suas implementações concretas.

Diagrama UML:

<img width="726" height="390" alt="image" src="https://github.com/user-attachments/assets/744b2bee-f383-4a50-bb07-a0d2890050a3" />

imagem do site: https://refactoring.guru/pt-br/design-patterns/strategy

Código de exemplo e com explicação (retirado do site: https://refactoring.guru/pt-br/design-patterns/adapter/python/example):

<img width="718" height="400" alt="image" src="https://github.com/user-attachments/assets/d96cd7af-2bb1-45c8-a159-7170c50f8dfb" />

Context (Contexto): Define a interface de interesse para os clientes, mantém uma referência a um objeto Strategy e delega parte do trabalho para esse objeto e pode alterar a estratégia em tempo de execução.

<img width="453" height="303" alt="image" src="https://github.com/user-attachments/assets/638fbb6d-f916-44dd-a725-769089898934" />

Strategy (Estratégia): Define uma interface comum para todas as versões suportadas de algum algoritmo e é utilizada pelo Context para chamar o algoritmo definido pelas Concrete Strategies.

ConcreteStrategyA e ConcreteStrategyB: Implementam o algoritmo seguindo a interface base Strategy e são intercambiáveis no Context.

<img width="521" height="189" alt="image" src="https://github.com/user-attachments/assets/c4eed077-377e-4d22-a101-9c90b90c1ce9" />

if __name__ == "__main__":
Esse bloco demonstra o uso do padrão Strategy. Nele, um objeto Context é criado com uma estratégia inicial, a lógica de negócios é executada e, em seguida, a estratégia é alterada. Isso permite mostrar, na prática, como o padrão Strategy oferece flexibilidade para trocar algoritmos em tempo de execução sem modificar o código cliente.






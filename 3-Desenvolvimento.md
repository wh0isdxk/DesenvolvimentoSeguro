# Desenvolvimento 

<p align="center">  
<img src="https://media.giphy.com/media/7TcdtHOCxo3meUvPgj/giphy.gif" width="182"/>

</p>


Essa é a etapa onde aplicamos os conceitos de **Desenvolvimento Seguro e as Boas Práticas** referentes a cada linguagem, também sendo aplicados a *Patterns* e *Frameworks*, atendendo aos requisitos da etapa anterior. 

Aqui também podemos usar o **OWASP TOP 10** para prevenir vulnerabilidades que são mais comuns, segue a lista: 

    1. Injeção
    2. Quebra de Autenticação
    3. Exposição de Dados Sensíveis
    4. Entidades Externas de XML (XXE)
    5. Quebra de Controle de Acessos
    6. Configurações de Seguranças Incorretas 
    7. Cross-Site Scripting (XSS)
    8. Desserialização Insegura 
    9. Utilização de Componentes/Recursos Vulneráveis 
    10. Monitoração Insuficiente 

Podemos incluir alguns controles que contribuirão para que o nosso código seja seguro, além de já definir os recursos de segurança que foram feitos no passo anterior. 

O uso de Frameworks e Bibliotecas seguras, e também sempre mantê-las atualizadas afim de evitar novas vulnerabilidades. Entretanto tenha em mente que não se deve considerar que por um framework esta *up-to-date* ele está livre de vulnerabilidades. É necessário sempre mitigar ataques durante o design da aplicação. Assumir que vulnerabilidades seriam evitadas ao se manter estes frameworks atualizadas seria errado por dois motivos:

- Boa parte das vulnerabilidades encontradas são devido ao design da aplicação e independente do framework ou linguagem utilizados.
- Muitos desses frameworks utilizam pacotes e plug-ins que não necessariamente passaram por um processo rigoroso de revisão em segurança.

Ref.: 👆🏼 The web application hackers handbook

Garantir a política de mínimo acesso, e que esse acesso seja seguro, ao Banco de Dados. Aqui também vale ressaltar que, se há o tráfego desses dados, é importante que eles sejam feitos de forma segura, encriptados. Aqui vale ressaltar também, que o código fonte deve estar em um lugar seguro e é importsnte validar que não há nenhum escape de dados. 

Outro ponto é a implementação de logs de segurança e monitoramento, além de garantir o controle de performance, você passa a ter visibilidade do seu sistema, dessa forma detectando qualquer comportamento estranho e/ou pessoas más intencionadas que possam tentar subir códigos maliciosos. 

O tratamento de erros e excessões também é um tópico importante, se ele não for feito da maneira correta, uma pessoa pode facilmente detectar o problema e tentar escalar alguma vulnerabilidade em cima disso.

## Lidando com entradas fornecidas pelo usuário.

Existe uma importante concepção que deve ser considerada para qualquer um que trabalhe com sistemas de software que possuem interação com o usuário: **toda entrada fornecida deve ser considerada uma tentativa de ataque.** Grande parte dos ataques contra aplicações envolvem submeter entradas inesperadas gerando resultados que não eram os esperados pelos desenvolvedores. Consequentemente estes resultados podem entregar não somente dados, privilégios e informações confidenciais, mas em último caso abrir uma porta de entrada para atacantes aos servidores. Abaixo estão as possíveis abordagens que podem ser utilizadas.

### *Reject Known Bad*

Seria basicamente rejeitar toda e qualquer entrada que não é reconhecida como pela lista de entradas possíveis à aplicação. Por exemplo em uma aplicação que se deseja previnir SQL injection, comandos SQL(e.g.: SELECT, FROM, INSERT) devem pertencer a lista das entradas proibidas. Entretando, existe um problema que você já deve ter notado, esta abordagem é extremamente limitada. Pelos seguintes motivos:

- Nunca um desenvolvedor irá cobrir todas as possiveis strings que poderiam ser passadas e que representariam tentativas de ataques.
- Ao tentar cobrir uma específica, surgiriam outras 10, 20, 30.
- Ou seja, esta abordagem, em termos práticos não é possível.

### *Accept Known Good*

É exatemente o oposto da anterior. Isto é, a aplicação aceitará somente entradas dos quais sabe que são confiaveis. Esta abordagem é uma das melhores formas de mitigar ataques, porém ainda possui um problema: é extremamente inflexivel a mudanças. Se uma aplicação é usada mundialmente e possuirá as mais variadas formas de entrada esta opção seria impraticável.

### *Sanitization e Safe data handling*

Essa abordagem assume que algumas vezes a entrada fornecida precisa ser reconfigurada e reescrita para ser aceita. O processo de "escapar" um caracter especial é um processo de sanitização. Entretando por muitas vezes não um procedimento que chegue a evitar um ataque. Já o *safe data handling* assume que o dado precisa ser validado antes de ser utilizado. Um exemplo seria a parametrização de queries em SQL.


### *Multistep validation and Canonicalization*

É o processo de, ao detectar possíveis entradas que indicam ataques, realizar a sanitização e a passagem de uma entrada válida ao o componente posterior. Entretanto existem problemas com relação a esta abordagem assim como existiu na primeira abordagem *Reject Known Bad*. Nunca será possível para um desenvolvedor cobrir todos os cenários tão variados eles são. Temos o exemplo em XSS.

Queremos evitar Cross-site Scripting retirando a palavra `<script>` de toda e qualquer string. Isto é:

````
<script>alert(document.cookie)</script>

se tornará

alert(document.cookie)
````

Mas agora imagine que um atacante note este padrão e passe a enviar a seguinte entrada:

```
<scr<script>ipt>alert(document.cookie)</scr<script>ipt>

se tornará...

<script>alert(document.cookie)</script>
```

### *Boundary validation*

É o processo de validação e sanitização da entrada a cada passo de componente. Significa que o frontend não confiaria na entrada fornecido pelo usuário, fazendo-o obedecer um padrão. O backend ao receber a entrada também fará uma sanitização e uma validação da entrada. Ao passar para a camada de dados, o banco também parametrizará o dado de entrada. Ou seja, basicamente a cada "passagem de bastão" o componente anterior e posterior faz uma validação e sanitização da saída/entrada. Esta é uma das forma mais eficaz de se previnir que entradas maliciosas sejam recebidas por cada um de seus componentes visto que se estaria modularizando as validações de acordo com cada tipo de componente (e.g.: frontend, backend, banco de dados).

Trazendo em tópicos, seguem as checklists da OWASP que trazem pontos super importantes para validação em cada etapa. 

- Controle de Acessos 
- Validação dos Dados de Entrada
- Validação dos Dados de Saída 
- Autenticação e Gerenciamento de Credenciais 
- Gerenciamento de Sessões 
- Práticas de Criptografia
- Tratamento de Erros e Log
- Proteção de Dados 
- Segurança nas Comunicações
- Configuração do Sistema 
- Segurança em Banco de Dados 
- Gerenciamento de Arquivos 
- Gerenciamento de Memória 
- Práticas Gerais de Codificação

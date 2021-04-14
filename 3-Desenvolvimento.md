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

O uso de Frameworks e Bibliotecas seguras, e também sempre mantê-las atualizadas afim de evitar novas vulnerabilidades. 

Garantir a política de mínimo acesso, e que esse acesso seja seguro, ao Banco de Dados. Aqui também vale ressaltar que, se há o tráfego desses dados, é importante que eles sejam feitos de forma segura, encriptados. Aqui vale ressaltar também, que o código fonte deve estar em um lugar seguro e é importsnte validar que não há nenhum escape de dados. 

Outro ponto é a implementação de logs de segurança e monitoramento, além de garantir o controle de performance, você passa a ter visibilidade do seu sistema, dessa forma detectando qualquer comportamento estranho e/ou pessoas más intencionadas que possam tentar subir códigos maliciosos. 

O tratamento de erros e excessões também é um tópico importante, se ele não for feito da maneira correta, uma pessoa pode facilmente detectar o problema e tentar escalar alguma vulnerabilidade em cima disso. 

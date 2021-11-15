<p align="center">

<img src="https://cdn0.iconfinder.com/data/icons/business-startup-10/50/8-512.png" width=300 height=300>

</p>

# Fundamentos

### O que é Desenvolvimento Seguro?


### Porque Desenvolvimento Seguro?
Quando falamos de desenvolvimento seguro, é importante pensar em todas as etapas que fazem parte do processo de SDLC:

```
 Requisitos > Design > Desenvolvimento > Testes > Deploy/Produção 
```

A maioria das empresas fazem validações de segurança nas ultimas fases dos projetos, e isso acaba por gerar um custo de correção bem maior do que seria caso as vulnerabilidades fossem tratadas ainda em fase inicial. 
Abaixo temos um gráfico resultado pela NIST que retrata esse cenário, uma vez que fazemos a mitigação desses problemas logo no início, evitamos o retrabalho, aumentamos o nível de maturidade de segurança, e prevenimos possiveis ataques baseados nessas vulnerabilidades. 

<p align="center">
<img src="https://assets.deepsource.io/032e723/images/blog/cost-of-fixing-bugs/chart.jpg" width=680>   
</p>




### Quais os pilares do Desenvolvimento Seguro?


### Por onde começar?

Antes de fornecer treinamentos sobre Desenvolvimento Seguro, e começar a aplicar os conceitos desde o início, é interessante saber o nível de maturidade de segurança do seu ciclo e a partir disso fazer as modificações necessárias para essa melhoria. 
Atualmente temos a OWASP SAMM (OWASP Software Assurance Maturity Model), um projeto mantido pela OWASP que visa ajudar numa avaliação rápida do contexto para entender o nível de maturidade. Ele é composto por algumas perguntas de acordo com cada uma das fases do processo de desenvolvimento:

- **Requisitos** - Durante o momento de construção do seu software, sua equipe tem como princípio realizar o levantamento das necessidade de segurança e privacidade?

- **Design** - Sua equipe, ao iniciar um novo projeto de software, realiza ações para identificar as ameaças as quais o seu software pode estar exposto?

- **Coding** - Existe algum tipo de avaliação do código (Code Review)?

- **Testes** - Durante a fase de testes de sua aplicação, testes estáticos afim de validar os requisitos de segurança definidos são realizados? 

- **Produção** - Quando da operacionalização do seu software, há a realização de pentests para garantir que sua aplicação está protegida?

Com base nos "sim" e "não" das respostas conseguimos ter uma ideia do nível de maturidade do processo, se o "não" for maioria, é importante que o assunto seja levado para discussão. 

### Shift Left 

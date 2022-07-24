# Testes

<p align="center">  
<img src="https://media.giphy.com/media/82MkOzEyyXeSLkgWyv/giphy.gif" width="208"/>

</p>

Aqui aplicamos os conceitos de análise de código, seja voltada para qualidade e/ou segurança do código. Assim como o tratamento e resolução das vulnerabilidades e problemas que forem encontrados nesse processo de análise e revisão. 

Algumas ferramentas podem nos ajudar nessa verificação, chamamos de SAST as ferramentas de análise de código estático, citando algumas delas:

Ferramentas opensource:

    > Sonarcube/Sonarcloud
    > CodeWarrior
    > Findbugs
    > ReshiftSecurity 
    > Codesec
    > Horusec
    > LGTM
    > ScoutSuite
    > HUSKYCI
  
Ferramentas pagas:

    > Github Advanced Security
    > Dependabot Alerts 
    > Veracode
    > Checkmarx CxSAST
    > Fortify
    
 Ferramentas com versāo Open Source:
 
    > Snyk Code

Nesse processo de análise, tanto na parte automatizada quanto na análise manual, alguns pontos são importantes de se considerar: 

    1. Falhas de injeção 
    2. Lançamentos de Erros e Exceções 
    3. Códigos Privilegiados 
    4. Força das Criptografias que estão sendo utilizadas 
    5. Cuidados com os comentários feitos no código 
    6. Vazamento de algum tipo de secret ou dados sensíveis
    
Exemplo de um pipeline com checagens de segurança

<img width="608" alt="DevSecOps_Toolchain" src="https://user-images.githubusercontent.com/46326549/180659993-140f6a44-d140-49ec-982b-6cd23c43b21f.png">



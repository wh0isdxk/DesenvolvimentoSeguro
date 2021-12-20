# Implementando a autenticação

Implementar uma autenticatição segura é, em boa parte das vezes, um *trade-off* entre UX e os requisitos de segurança. Entretanto como designer e desenvolvedor de sistemas é necessário ter em mente alguns fatores que fazem o balanço entre esses parâmetros.

- A criticidade de cyber-segurança é dada pela funcionalidade que a aplicação oferece.
- A grau com o qual os usuários lidarão com os diferentes tipos de controle de autenticação depende de aplicação para aplicação.
- Qual o custo de fornecer uma *pior* experiência do usuário que suporte a segurança.
- Como seus competidores realizam os mesmos controles?

## Utilize forte regras sobre credenciais

Existem algumas regras relacionadas as credenciais que devem estar presentes em todos os sistemas. São elas:

- Garanta uma qualidade minima para as senhas utilizadas no sistema. Exija uma quantidade minima de caracteres, misture letras maiúsculas e minúsculas, evite e previna senhas comuns e facilmente "advinhaveis".

## Trate as credenciais como secretas

- Toda senha deve ser validada em totalidade e sem alterações pelo servidor.
- As aplicações devem ativamente previnir qualquer tipo de ataque entre o processo de preenchimento de login e o login de fato. Qualquer exceção nesse meio tempo deve invalidar a sessão.
- Todo código relacionado à autenticação deve ser cuidadosamente revisado.
- Se a aplicação permitir que um usuário seja usado como *stub*, sua lógica e validação deve ser cuidadosamente revisada visto que isto permitirá um admin assumir como usuário logado qualquer usuário registrado.
- Logins que utilizado multiplos fatores devem previnir a interferência entre as validações:
    - Todo dado enviado deve ser validado no servidor.
    - Todo dado que foi enviado ao servidor não deve ser alterado por qualquer ação enviada pós-validação.
    - Todo estagio deve validar que os estagios anteriores, requiridos para o login foram passados e validados.
    - Se as validações falharem entre os estagios a aplicação não deve mostrar qualquer tipo de resposta ao lado do client. Apenas ao final de todo o processo o usuário deve ser avisado que o login falhou não entregando qualquer tipo de informação sobre o que falhou.

## Previnindo vazamento de informaçÕes

- Os múltiplos tipos de autenticação usados pela aplicação devem sempre proteger informações. Todo parâmetro em cada *query* deve sempre ser validado através do privilégio que cada usuário possui.
- Qualquer exceção desconhecida deve ser tratada e exposta como genérica. Sendo assim nenhuma informação é exposta a um atacante.
- Seguindo a lógica de "Não entregue informação" se a aplicação emprega *lock* de contas a mesma não deve dizer quantos minutos e quem sofreu o *lock*.
- Se a aplicação suporta que os próprios usuários se registrem, a aplicação deve:
    - Gerar *usernames* únicos e com um grau alto de entropia de tal forma que evite a predição de novos nomes.
    - A aplicação pode também utilizar os emails como *username* e neste caso deve enviar um email único que contenha uma URL imprevisível para o email registrado informando os usuários dos procedimentos que devem ser seguidos.

## Previnindo ataques força-bruta

- Implemente desafios quando ações importantes forem tomadas, como por exemplo: mudanças de senha e mudanças de email.
- Use *usernames*, quando possível, gerados automaticamente para previnir que um atacante advinhe os usuários registrados.
- Deve-se também balancear *lock* de contas com a possibilidade de reativa-las. Um sistema que trave as contas facilmente é também prejudicial ao sistema visto que um atacante pode forçar vários usuários a ficarem impossibilitados de logar.

## Previnindo mal uso da função de mudança de senha.
- A função só deve ser acessível através contas autenticadas e que estão mudando suas próprias senhas. O servidor deve sempre validar estas informações.
- E sempre que a senha for alterada o usuário deve ser avisado por outros meios de comunicação(emails, SMS).

## Previnindo mal uso da função de recuperação de conta

- Funcionalidade, como uso de dicas de senha, não devem ser NUNCA empregadas visto que elas podem dar pistas sobre qual tipo de senha esta sendo utilizada.
- A melhor solucão disponível é enviar um email que contenha uma URL única e com o grau de entropia que previna com que um atacante advinhe. Ela deve também ser limitada em questão de tempo de acesso e quantidade de acesso. Uma vez a URL utilizada deve ser expirada e um email de notificação deve ser enviado ao usuário.

## Log, Monitore e Notifique(!!!!)

- A aplicação deve logar toda e qualquer atividade que esteja relacionada a eventos de autenticação. Isto inclui login, logout, mudanças de senha, reset de senha, suspensão de conta e recuperação de conta.
- Anomalias durante o processo de autenticação devem ser processadas em tempo real e alertas devem ser disparados para previnir intrusos.
- Qualquer anomalia deve ser alertada ao usuário, seja ela crítica ou não.

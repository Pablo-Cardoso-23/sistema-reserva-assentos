# Sistema de reserva de assentos
Considere um sistema de reserva de assentos online para um cinema que possui 100 assentos numerados de 1 a 100. O sistema deve permitir que os clientes reservem assentos de forma eficiente e confiável. Vários clientes podem acessar o sistema simultaneamente, e cada cliente pode tentar reservar um ou mais assentos por vez. 
Sem mecanismos adequados de sincronização, o sistema está sujeito a condições de corrida (race conditions) quando dois ou mais clientes tentam reservar o mesmo assento ao mesmo tempo. Essas condições de corrida podem levar a problemas graves, como: 
1. Reservas duplicadas : Dois ou mais clientes podem acabar reservando o mesmo assento porque o sistema não verifica corretamente se o assento já está ocupado antes de confirmar a reserva. Isso ocorre quando duas threads (representando solicitações de reserva) leem o estado do assento ao mesmo tempo, determinam que ele está disponível e realizam a reserva independentemente.
2. Inconsistência no estado do sistema : O sistema pode exibir informações incorretas sobre a disponibilidade dos assentos, levando a uma experiência frustrante para os clientes. Por exemplo, um cliente pode ver que um assento está disponível, mas ao tentar reservá-lo, descobre que outro cliente já o reservou enquanto ele estava concluindo o processo.
3. Perda de atualizações : Quando múltiplas threads modificam o estado dos assentos simultaneamente sem controle adequado, algumas atualizações podem ser perdidas. Por exemplo, uma thread pode sobrescrever as alterações feitas por outra thread, resultando em perda de reservas válidas.

Para resolver esses problemas, é necessário implementar mecanismos de sincronização que garantam a exclusão mútua (mutual exclusion) no acesso aos dados compartilhados. Um mutex (trava) pode ser usado para garantir que apenas uma thread (representando uma solicitação de reserva) possa modificar o estado dos assentos por vez. Com isso, o sistema garante que: 
1. Cada assento seja reservado apenas uma vez. 
2. As informações exibidas sobre a disponibilidade dos assentos estejam sempre consistentes. 
3. As operações de reserva sejam processadas de forma segura e confiável. 

Além disso, o uso de técnicas avançadas de sincronização, como semáforos ou monitores, pode ser explorado para melhorar o desempenho do sistema e evitar gargalos desnecessários, garantindo que o sistema permaneça responsivo mesmo sob carga elevada. 

#  Objetivo

Implemente, em Python, o referido sistema de reservas, desenvolvendo o código em 2 (dois) módulos ou arquivos: a versão Servidor e a versão Cliente, usando sockets. Além desses arquivos, envie também instruções de como utilizar o sistema que seu grupo desenvolveu. 

Atenção: No módulo servidor, devem ser exibidas mensagens de todas as operações relacionadas no sistema (o que pode ser feito a partir de print’s). 

# Resumo Banco de Dados
## Laboratório 3

Criando um banco de dados na Azure
1. Primeiro a professora mostrou as VMs. Ao criar uma máquina virtual, é necessário configurá-la muito bem, escolhendo recursos como armazenamento, memória, processador, etc. Para isso, é preciso entender cada opção e suas implicações.

Correto. A criação de uma Máquina Virtual (VM) no Azure é um exemplo clássico de IaaS (Infraestrutura como Serviço). Nesse modelo, você tem controle total sobre o ambiente, mas também a responsabilidade de configurá-lo corretamente desde o início. A escolha de cada componente é uma decisão técnica e financeira crucial:

Tamanho (Size): A Azure oferece centenas de "tamanhos" de VMs, agrupados em séries (por exemplo, Série D para uso geral, Série E para aplicações com uso intensivo de memória, Série N para cargas de trabalho com GPU). A escolha do tamanho define a quantidade de vCPUs (processadores virtuais) e RAM (memória). Escolher um tamanho superdimensionado significa desperdiçar dinheiro, enquanto um subdimensionado causará lentidão e problemas de desempenho na sua aplicação.

Armazenamento (Discos): Você precisa escolher o tipo e o tamanho do disco do sistema operacional e de quaisquer discos de dados adicionais. As opções variam em performance e custo, indo desde HDDs Standard (mais baratos, para dados acessados com pouca frequência) até SSDs Premium e Ultra Disks (mais caros, para aplicações que exigem altíssima velocidade de leitura e escrita, como bancos de dados transacionais).

Imagem (Image): Refere-se ao sistema operacional pré-instalado, como Windows Server 2022 ou diversas distribuições Linux (Ubuntu, Red Hat). A escolha impacta não apenas a compatibilidade do seu software, mas também o custo, já que licenças de Windows são cobradas, enquanto muitas de Linux são gratuitas.

Entender essas implicações é fundamental porque, em um ambiente IaaS como uma VM, você é quem gerencia o sistema operacional, as atualizações de segurança, o monitoramento de desempenho e a instalação de todo o software necessário, incluindo o próprio sistema de banco de dados.

2. Para criar um banco de dados, é preciso especificar um servidor simbólico (não físico, é o servidor do banco de dados para autenticar o usuário, entre outras coisas).

Exatamente. Esse conceito é um dos pontos centrais dos serviços de PaaS (Plataforma como Serviço), como o Banco de Dados SQL do Azure ou o Banco de Dados do Azure para MySQL/PostgreSQL. O que você cria não é um servidor físico ou uma VM, mas um servidor lógico (ou "simbólico").

Este servidor lógico funciona como um ponto de administração centralizado para um ou mais bancos de dados. Suas principais funções são:

Ponto de Conexão (Endpoint): Ele fornece um nome de servidor único e público (ex: meuservidor.database.windows.net) que suas aplicações usarão para se conectar aos bancos de dados. A Azure gerencia toda a infraestrutura física por trás desse endereço.

Gerenciamento de Segurança: É no nível do servidor lógico que você configura as regras de firewall, definindo quais endereços IP têm permissão para acessá-lo.

Autenticação e Autorização: Ele gerencia os logins de acesso. Você pode usar a autenticação SQL (usuário e senha) ou a autenticação do Azure Active Directory, e é no servidor lógico que essas credenciais são validadas antes de permitir o acesso a um banco de dados específico.

Ao usar um servidor lógico, a Azure abstrai toda a complexidade da infraestrutura subjacente. Você não precisa se preocupar com o sistema operacional, patches de segurança do SO ou hardware. Você foca apenas em gerenciar o servidor lógico e seus bancos de dados.

3. Recapitulação sobre IaaS e SaaS: quanto mais nós estivermos envolvidos no gerenciamento do serviço, menos a provedora de nuvem estará. Ou seja, no IaaS nós temos muito mais responsabilidades do que na SaaS. Nisso consiste o modelo de responsabilidade compartilhada.

Perfeito. Essa é a essência do Modelo de Responsabilidade Compartilhada (Shared Responsibility Model), um conceito fundamental em computação em nuvem. Ele define claramente quais tarefas de segurança e gerenciamento são de responsabilidade da Microsoft (a provedora) e quais são de sua responsabilidade (o cliente). A divisão varia drasticamente conforme o modelo de serviço:

IaaS (Infraestrutura como Serviço - ex: Máquinas Virtuais): A Microsoft é responsável pela infraestrutura física: os datacenters, a rede física, os servidores físicos. Sua responsabilidade é muito grande: proteger e gerenciar o sistema operacional (aplicar patches), configurar a rede virtual, gerenciar o acesso dos usuários, proteger os dados, instalar e gerenciar as aplicações. Você tem o maior controle, mas também o maior fardo de gerenciamento.

PaaS (Plataforma como Serviço - ex: Banco de Dados SQL do Azure): A responsabilidade da Microsoft aumenta. Além da infraestrutura física, ela também gerencia o sistema operacional e o ambiente de execução (neste caso, o software do SQL Server). Sua responsabilidade diminui: você ainda precisa gerenciar a segurança da rede (firewall), o controle de acesso e, o mais importante, proteger seus próprios dados e aplicações que se conectam ao banco.

SaaS (Software como Serviço - ex: Microsoft 365 / Office 365): A Microsoft tem a responsabilidade máxima. Ela gerencia tudo: a infraestrutura, o sistema operacional, a plataforma e o próprio software. Sua responsabilidade é a mínima, focando-se quase que exclusivamente em gerenciar o acesso dos seus usuários e proteger os dados que você insere no serviço.

Compreender este modelo é vital para garantir a segurança e a conformidade de qualquer solução na nuvem, pois deixa claro que, mesmo em um ambiente gerenciado pela Microsoft, a segurança dos seus dados e do acesso a eles será sempre uma responsabilidade sua.

# Resumo Máquina Virtual
## Laboratório 2

SLA e Máquinas Virtuais

1. SLA significa "Service Level Agreement", que basicamente determina o tempo máximo pelo qual um serviço contratado ficará indisponível. Se o tempo de indisponibilidade superar o limite, o usuário poderá ser ressarcido pelo valor que perdeu.

Exato. O SLA, ou Acordo de Nível de Serviço, é um compromisso formal assumido pela Microsoft sobre a disponibilidade e o desempenho de um serviço do Azure. Ele é expresso em porcentagens, como 99,9% ou 99,99% de tempo de atividade ("uptime"). Essa porcentagem se traduz em um tempo máximo de inatividade permitido durante um período, geralmente um mês. Por exemplo, um SLA de 99,9% permite cerca de 43 minutos de indisponibilidade por mês.

Caso a Microsoft não cumpra essa promessa e o serviço fique indisponível por mais tempo que o permitido, a empresa oferece uma compensação. Esse ressarcimento não é automático; o cliente precisa abrir um chamado de suporte para solicitar os "créditos de serviço". O valor do crédito é geralmente um percentual da fatura mensal daquele serviço específico, variando conforme a gravidade da falha. É fundamental entender que o SLA se aplica a serviços em sua versão final ("General Availability") e não aos que estão em fase de testes ("preview").

2. O portal contém pontos de interrogação flutuantes ao lado de nomes/conceitos/categorias que dão uma pequena explicação sobre o que está se referindo, facilitando o aprendizado. Além disso, eles têm um link para a documentação.

Essa é uma das características mais úteis do portal do Azure para iniciantes e até mesmo para usuários experientes. Esses ícones de ajuda contextual, geralmente representados por um ponto de interrogação (?), são chamados de "tooltips" ou dicas de ferramenta. Ao passar o mouse sobre eles, uma pequena janela se abre com uma explicação clara e concisa sobre o recurso, a configuração ou o campo ao lado.

Essa funcionalidade transforma o portal em uma ferramenta de aprendizado interativa. Em vez de precisar sair da tela para pesquisar um termo, o usuário obtém a informação necessária instantaneamente. O link "Saiba mais" (ou "Learn more"), que acompanha essas dicas, é um atalho direto para a Microsoft Learn, a plataforma de documentação oficial. Isso permite que o usuário aprofunde seus conhecimentos, acesse tutoriais, guias de início rápido e exemplos práticos relacionados àquela funcionalidade específica, criando uma ponte direta entre a prática e a teoria.

3. A professora demonstrou brevemente as zonas de disponibilidade e explicou como elas se relacionam com os níveis do SLA. Duplicação de dados envolve um maior tempo de disponibilidade, o que afeta diretamente o custo da contratação.

As Zonas de Disponibilidade são um conceito fundamental para construir sistemas resilientes a falhas no Azure. Uma "Região" do Azure (como "Leste dos EUA" ou "Sul do Brasil") é uma área geográfica que contém um ou mais datacenters. Dentro de uma mesma Região, as Zonas de Disponibilidade são datacenters fisicamente separados, cada um com sua própria fonte de energia, refrigeração e rede independentes.

Ao configurar um serviço, como uma máquina virtual ou um banco de dados, para usar Zonas de Disponibilidade, você está, na prática, criando cópias ou réplicas dele em locais diferentes, mas próximos. Se um datacenter inteiro falhar (por exemplo, devido a uma queda de energia ou um problema de rede), a cópia em outra Zona de Disponibilidade assume a operação, garantindo que sua aplicação continue funcionando.

Essa redundância aumenta drasticamente a tolerância a falhas, permitindo que a Microsoft ofereça um SLA muito mais alto (por exemplo, 99,99%) para serviços configurados dessa maneira. Naturalmente, essa maior garantia tem um custo: você paga pelos recursos duplicados e pela transferência de dados entre as zonas. Portanto, há uma relação direta: maior disponibilidade e um SLA mais robusto exigem uma arquitetura mais complexa e, consequentemente, um investimento maior.

4. Sempre lembre-se do propósito de utilizar um serviço para saber qual plano, SLA e configuração utilizar.

Este é o princípio mais importante na gestão de custos e na arquitetura de soluções em nuvem. A escolha de cada serviço e sua configuração deve ser uma decisão de negócio, não apenas técnica. Antes de criar qualquer recurso no Azure, é crucial perguntar: "Qual é o objetivo deste serviço?".

Ambiente de desenvolvimento ou teste: A criticidade é baixa. Falhas não impactam o cliente final. Portanto, pode-se usar os planos mais baratos, com SLAs mais baixos (ou até mesmo sem SLA), e evitar configurações caras como a replicação entre Zonas de Disponibilidade.

Aplicação interna da empresa: A importância é média. Uma indisponibilidade pode atrapalhar o trabalho dos funcionários, mas talvez não precise de uma resposta imediata. Um SLA intermediário, como 99,9%, pode ser suficiente.

E-commerce ou sistema crítico para o cliente: A criticidade é altíssima. Cada minuto fora do ar representa perda de receita e dano à reputação. Aqui, o investimento é justificado. É essencial escolher planos com o SLA mais alto possível (99,99% ou mais) e usar todos os recursos de resiliência disponíveis, como as Zonas de Disponibilidade.

Ignorar esse princípio leva a dois problemas comuns: gastar muito mais do que o necessário em sistemas não críticos ou, pior ainda, economizar em sistemas essenciais e sofrer grandes prejuízos quando ocorrer uma falha.

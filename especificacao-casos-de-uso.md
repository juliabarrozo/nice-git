

# 📝 Especificação de Caso de Uso

## 1. Introdução
Explique o objetivo desta especificação e como ela detalha cada funcionalidade.  

## 2. Modelo de Tabela
Preencha uma tabela como esta para cada caso de uso:

| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Cadastrar Colaboradores|
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa  o menu “Gestão de Colaboradores” no canto superior esquerdo <br> 5. Sistema exibe a tela de colaboradores. <br> 6. Administrador clica em “Novo Cadastro”. <br> 7. Sistema exibe formulário de cadastro <br> 8. Administrador insere dados obrigatórios (Nome, E-mail, CPF, Cargo) <br> 9.  Administrador escolhe o Tipo de Colaborador: Administrador, Colaborador, Gestor ou Psicólogo <br> 10. Administrador confirma em “Salvar” <br> 11. Sistema valida os dados e registra o colaborador. |
| **Fluxos Alternativos** | 1. Dados inválidos → Sistema exibe mensagem de erro <br> 2. CPF já cadastrado → Sistema exibe mensagem de duplicidade. |
| **Pós-condições**     | O colaborador/administrador/gestor/psicólogo é incluído no sistema |
| **Regras de negócio** | 1. Apenas usuários autenticados (Administrador) podem cadastrar colaboradores. <br> 2. O campo “Tipo de Colaborador” deve ser obrigatório <br> 3.  Cada CPF deve ser único no sistema  |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Editar Colaborador |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | O administrador já está autenticado no sistema e o colaborador já deve ter sido cadastrado |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa a aba “Cadastros” no canto superior esquerdo <br> 5. Sistema exibe a tela de colaboradores. <br> 6. Administrador seleciona um colaborador existente <br> 7. Administrador clica no botão “Editar” <br> 8. Sistema exibe formulário com dados preenchidos. <br> 9. Administrador altera as informações desejadas. <br> 10. Administrador clica em “Salvar Alterações”. <br> Sistema atualiza os dados do colaborador.  |
| **Fluxos Alternativos** | 1. Dados inválidos → Sistema exibe mensagem de erro |
| **Pós-condições**     | O colaborador tem seus dados atualizados no sistema |
| **Regras de negócio** | 1. Apenas usuários autenticados (Administrador) podem editar informações de colaboradores. <br> 2. Alteração de tipo (Administrador, Colaborador, Gestor, Psicólogo) deve ser registrada em log de auditoria|


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Excluir Colaborador |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | O administrador já está autenticado no sistema e o colaborador já deve ter sido cadastrado |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa a aba “Cadastros” no canto superior esquerdo <br> 5. Sistema exibe a tela de colaboradores. <br> 6. Administrador seleciona um colaborador existente <br> 7. Administrador clica no botão “Excluir” <br> 8. Sistema exibe mensagem de confirmação “Deseja realmente excluir ?” 9. Administrador confirma exclusão. <br> 6. Sistema remove o colaborador do banco de dados  | 
| **Fluxos Alternativos** | Administrador cancela a exclusão → Sistema mantém colaborador ativo |
| **Pós-condições**     | O colaborador é removido do sistema |
| **Regras de negócio** | 1. Apenas usuários autenticados (Administrador) podem exluir todos os tipos de colaboradores. <br> 2.Não é permitido excluir o último Administrador ativo no sistema |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Consultar Colaborador |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema e existir colaboradores cadastrados. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa  o menu “Gestão de Colaboradores” no canto superior esquerdo <br> 5 . Sistema exibe a tela de colaboradores. <br> 6. Administrador usa a barra de busca para pesquisar por nome, CPF, e-mail ou tipo de colaborador ou pode aplicar filtros (tipo : Administrador, Colaborador, Gestor ou Psicólogo) <br> 7. Sistema exibe os resultados da pesquisa/lista filtrada. <br> 8. Administrador seleciona um colaborador para visualizar informações detalhadas. <br> 9. Sistema apresenta uma tela/modal com os dados completos do colaborador (nome, e-mail, tipo, status, data de cadastro). |
| **Fluxos Alternativos** | 1. Nenhum colaborador encontrado → Sistema exibe mensagem “Nenhum resultado encontrado” <br> 2. Falha de conexão → Sistema exibe mensagem “Erro de conexão. Tente novamente mais tarde” |
| **Pós-condições**     | O administrador visualiza informações completas do colaborador selecionado. |
| **Regras de negócio** | 1.  A consulta deve permitir busca por múltiplos critérios (nome, CPF, e-mail, tipo) <br> 2. Somente administradores podem visualizar todos os dados do colaborador . |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Realizar Login |
| **Ator Principal**    | Gestor, Administrador, Colaborador, Psicólogo |
| **Pré-condições**     | Ator principal já cadastrado no sistema |
| **Fluxo Principal**   | 1. Usuário acessa a tela inicial do sistema <br> 2. Sistema exibe o formulário de login com os campos “E-mail” e “Senha”, além dos botões “Entrar”, “Esqueci minha senha” e “Cadastrar-se” <br> 3. O usuário insere os dados obrigatórios: E-mail e Senha <br> 4.O usuário clica no botão “Entrar” <br> 5. O sistema valida as credenciais informadas <br> 6. Caso os dados estejam corretos, o sistema identifica o tipo de usuário (Administrador, Gestor, Colaborador ou Psicólogo) <br> 7. O sistema redireciona o usuário autenticado para o painel principal correspondente ao seu perfil: (Administrador: Painel de Gestão Geral do Sistema ), (Gestor: Painel de Indicadores e Feedbacks da Equipe), (Psicólogo: Painel de Análise de Questionários e Relatórios), (Colaborador: Painel de Participação em Questionários e Envio de Feedbacks).|
| **Fluxos Alternativos** | 1.Senha incorreta ou usuário inexistente: Sistema exibe mensagem “E-mail ou senha inválidos. Tente novamente.” <br> 2. Campo obrigatório em branco: Sistema exibe mensagem “Preencha todos os campos obrigatórios.” <br> 3. Falha de conexão: Sistema exibe mensagem “Erro de conexão. Verifique sua internet e tente novamente.” |
| **Pós-condições** | 1. Ator principal autenticado no sistema <br> 2. O sistema registra o data/horário e tipo de usuário <br> 3. O ator principal tem acesso à interface inicial de acordo com o seu perfil de permissão. |
| **Regras de negócio** | 1. O campo Senha deve conter no mínimo 8 caracteres e incluir letras e números. <br> 2. O campo E-mail deve seguir o formato válido (ex: exemplo@empresa.com). <br> 3. O sistema deve bloquear o acesso após 3 tentativas incorretas consecutivas. <br> 4. Usuários inativos por mais de 90 dias devem ser bloqueados até revalidação de acesso. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Cadastrar Questionário |
| **Ator Principal**    | Psicólogo, Gestor de Equipe, Colaborador |
| **Pré-condições**     | 1. Ator principal já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Usuário acessa o painel principal do sistema. <br> 2. O sistema valida as credenciais e exibe o menu lateral. <br> 3. O usuário seleciona a opção “Questionários” no menu. <br> 4. O sistema exibe a tela de gerenciamento de questionários, contendo os botões “Novo Questionário”, “Editar”, “Excluir” e “Consultar” <br> 5. O usuário clica em “Novo Questionário”. <br> 6. O sistema exibe um formulário de criação de questionário, com os seguintes campos obrigatórios: Título do Questionário, Descrição, Categoria (ex: Bem-estar, Satisfação), Data de Criação (gerada automaticamente pelo sistema), Questões (campo dinâmico para adicionar perguntas abertas e/ou fechadas), Tipo de Resposta (Escala de 1 a 5, Múltipla escolha, Texto livre) <br> 7. O usuário preenche todos os campos obrigatórios. <br> 8. O usuário clica no botão “Salvar”. <br> 9. O sistema valida os dados inseridos, verifica campos obrigatórios e consistência das informações. <br> 10. O sistema registra o novo questionário no banco de dados, e adiciona automaticamente status (não respondido) e exibe a mensagem “Questionário cadastrado com sucesso!”. |
| **Fluxos Alternativos** | 1. Campos obrigatórios não preenchidos: Sistema exibe mensagem “Preencha todos os campos obrigatórios.” <br> 2. Erro de conexão: Sistema exibe mensagem “Erro de conexão. Tente novamente mais tarde.” <br> 3. Erro no banco de dados: Sistema exibe mensagem “Falha ao salvar o questionário. Contate o suporte.” |
| **Pós-condições**     | 1. O questionário é incluído com sucesso no sistema. <br> 2. O novo questionário passa a estar disponível na lista de questionários ativos para visualização, edição ou aplicação. |
| **Regras de negócio** | 1. Todos os campos marcados como obrigatórios devem ser preenchidos antes do salvamento. <br> 2. Cada questionário deve possuir um título único. <br> 3. O sistema deve registrar a data/hora do cadastro. <br> 4. Questionários só podem ser criados pelos (Psicólogos). <br> 5. O questionário deve seguir o padrão interno de avaliação de felicidade (mínimo de 5 questões, máximo de 20). <br> 6. Deve ser adicionado automaticamente um status após a criação (não respondido) |



| Item                  | Descrição |
|-----------------------|-----------|
| **Nome** | Editar questionário |
| **Ator Principal** | Psicólogo, Gestor de Equipe, Colaborador |
| **Pré-condições** | 1. Usuário já está autenticado no sistema <br> 2. O questionário desejado já deve ter sido previamente criado e salvo no sistema. |
| **Fluxo Principal** | 1. Usuário acessa o painel principal do sistema. <br> 2. O sistema valida as credenciais e libera acesso ao menu lateral. <br> 3. O usuário seleciona o menu “Questionários” localizado no canto superior esquerdo. <br> 4. O sistema exibe a tela de gerenciamento de questionários, apresentando a lista de questionários existentes com colunas de Título, Categoria, Data de Criação, Autor e Status. <br> 5. O usuário utiliza a barra de busca ou filtros (por categoria, período ou status) para localizar o questionário desejado. <br> 6. O usuário seleciona o questionário e clica no botão “Editar”. <br> 7. O sistema abre o formulário de edição do questionário, exibindo os campos: Título do Questionário, Descrição, Categoria, Questões (com opção de adicionar, remover ou modificar perguntas), Tipo de Resposta (Escala de 1 a 5, Múltipla escolha, Texto livre) <br> 8. O usuário realiza as alterações desejadas nas questões, textos ou categorias. <br> 9. O usuário clica no botão “Salvar Alterações” localizado no final do formulário. <br> 10. O sistema valida as informações alteradas, verifica a consistência dos dados e atualiza o questionário no banco de dados. <br> 11. O sistema exibe a mensagem “Questionário atualizado com sucesso!”.  |
| **Fluxos Alternativos** | 1. Campos obrigatórios não preenchidos: Sistema exibe a mensagem “Preencha todos os campos obrigatórios.” <br> 2. Erro de conexão ou falha no servidor: Sistema exibe a mensagem “Erro ao salvar alterações. Tente novamente mais tarde.” <br> 3. Usuário sem permissão: Sistema exibe a mensagem “Você não tem permissão para editar este questionário.” |
| **Pós-condições** | 1. O questionário é atualizado com sucesso no sistema. <br> 2. As novas informações substituem as antigas e ficam disponíveis para consulta e aplicação. <br> 3. O sistema registra em log o usuário responsável pela edição e a data/hora da modificação. |
| **Regras de negócio** | 1. Questionários só podem ser editados pelos (Psicólogos e Gestores de Equipe). <br> 2. Todos os campos obrigatórios devem ser validados antes da atualização. <br> 3. Alterações devem ser registradas no log de auditoria (usuário, data, hora, campos modificados). <br> 4. Não é permitido editar perguntas que já possuam respostas associadas <br> 5. A estrutura mínima do questionário deve conter pelo menos 5 perguntas antes de ser salvo. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Excluir questionário |
| **Ator Principal**    | Psicólogo, Gestor de Equipe, Colaborador |
| **Pré-condições**     | 1.  Ator principal já está autenticado no sistema <br> 2. O questionário desejado já deve ter sido previamente criado e salvo no sistema.|
| **Fluxo Principal**   | 1. Usuário acessa o painel principal do sistema. <br> 2. O sistema valida as credenciais e libera acesso ao menu lateral. <br> 3. O usuário  acessa o menu “Questionários” localizado no canto superior esquerdo <br> 4. Sistema exibe a lista de questionários disponíveis <br> 5. Usuário seleciona um questionário existente <br> 6. O usuário clica no botão “Excluir” <br> 8. Sistema exibe mensagem de confirmação: “Deseja realmente excluir este questionário?” <br> 9. O usuário confirma a exclusão <br> 10. Sistema remove o questionário do banco de dados e exibe a mensagem “Questionário excluído com sucesso” | 
| **Fluxos Alternativos** | 1. Usuário cancela a exclusão → Sistema mantém o questionário ativo <br> 2. Falha na exclusão (erro de conexão ou restrição de integridade) → Sistema exibe mensagem de erro “Não foi possível excluir o questionário. Tente novamente.” |
| **Pós-condições** | O questionário é removido do sistema e não aparece mais na lista de questionários ativos |
| **Regras de negócio** | 1. Questionários só podem ser excluídos pelos (Psicólogos e Gestores de Equipe). <br> 2. Toda exclusão deve ser registrada no log de auditoria (data, hora e usuário responsável). <br> 3. Não é permitido excluir perguntas que já possuam respostas associadas  |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Consultar questionário |
| **Ator Principal**    | Psicólogo, Gestor de Equipe, Colaborador|
| **Pré-condições**     | 1. Ator principal já está autenticado no sistema e existir colaboradores cadastrados. <br> 2. Deve haver questionários previamente cadastrados no sistema. |
| **Fluxo Principal**   | 1. Usuário acessa o painel principal do sistema. <br> 2. O sistema valida as credenciais e libera acesso ao menu lateral. <br> 3. O usuário acessa o menu “Questionário”, localizado no canto lateral esquerdo da tela. <br> 4. O sistema exibe a tela com o questionário disponível, apresentando sua lista de questões em escala likert. |
| **Fluxos Alternativos** | 1. Nenhum questionário encontrado → O sistema exibe a mensagem “Nenhum resultado encontrado.” <br> 2. Falha de conexão → O sistema exibe a mensagem “Erro de conexão". Tente novamente mais tarde.” <br> 3. Tentativa de acesso não autorizado → O sistema exibe a mensagem “Você não possui permissão para visualizar este questionário.” |
| **Pós-condições** | 1. O ator principal visualiza as informações completas do questionário selecionado. <br> 2. As consultas realizadas podem ser registradas no log do sistema para fins de auditoria. |
| **Regras de negócio** | 1. A consulta deve permitir busca e filtragem por múltiplos critérios (título, colaborador, categoria, período, status). <br> 2. Questionários com respostas anônimas devem ocultar dados de identificação do colaborador, em conformidade com a LGPD. <br> 3. Apenas usuários autenticados (Psicólogo, Gestor ou Colaborador) podem visualizar os questionários correspondentes ao seu nível de permissão. <br> 4. O sistema deve garantir que usuários comuns (Colaboradores) só visualizem questionários associados a si mesmos. <br> 5. O sistema deve registrar data, hora e usuário de cada consulta em log de auditoria. <br> 6. Somente podem ser visualizados questionários (respondidos) |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Criar Feedback  |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa o menu “Feedback” no canto superior esquerdo <br> 5. Sistema exibe a opção “Novo Feedback” <br> 6. Administrador clica em “Criar Feedback” <br> 7. Sistema exibe formulário com os campos: Título, Descrição, Categoria (Elogio, Crítica, Sugestão), Tipo de Envio (Anônimo ou Identificado) <br> 8. Colaborador preenche os campos e confirma clicando em “Enviar” <br> 9. Sistema valida os dados e registra o feedback no banco de dados <br> 10. Sistema exibe mensagem de sucesso “Feedback enviado com sucesso” |
| **Fluxos Alternativos** | F1. Dados não preenchidos - Sistema exibe mensagem de erro <br> F2. Erro de conexão - Sistema exibe mensagem de falha ao enviar |
| **Pós-condições**| 1. O feedback é registrado no sistema e fica disponível para consulta do administrador e do colaborador (se identificado)|
| **Regras de negócio** | 1.O feedback anônimo não deve armazenar dados pessoais <br> 2. O título e a descrição são campos obrigatórios <br> 3. Cada feedback deve ser vinculado á data e hora de envio |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Consultar Feedback  |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Usuário acessa o menu “Feedbacks” no canto superior esquerdo <br> 5. Sistema exibe a lista de feedbacks <br> 6 .Administrador  pode utilizar a barra de busca para localizar feedbacks por palavra-chave <br> 7. Administrador pode aplicar filtros (por data, categoria ou tipo) <br> 8. Sistema exibe resultados filtrados <br> 9. Administrador seleciona um feedback e clica em “Visualizar” <br> 10. Sistema exibe o feedback completo com data, categoria, tipo e status |
| **Fluxos Alternativos** | F1. Nenhum feedback encontrado → Sistema exibe “Nenhum resultado encontrado” <br> F2. Falha de conexão → Sistema exibe mensagem de erro |
| **Pós-condições**| 1. O usuário visualiza os detalhes do feedback selecionado |
| **Regras de negócio** | 1. Apenas usuários autenticados (Administrador e Colaborador) podem visualizar os feedbacks correspondentes ao seu nível de permissão. <br> 4. O sistema deve garantir que usuários comuns (Colaboradores) só visualizem feedbacks associados a si mesmos. <br> 3. Feedbacks anônimos não exibem dados de identificação do autor |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Editar Feedback  |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa o menu “Feedbacks” no canto superior esquerdo <br> 5. Sistema exibe a lista de feedbacks enviados  <br> 6. Administrador seleciona um feedback e clica em “Editar” <br> 7. Sistema exibe o formulário preenchido com os dados atuais <br> 8. Administrador altera os campos desejados (Título, Descrição, Categoria) <br> 9.Clica em “Salvar Alterações” <br> 10. Sistema valida os dados e atualiza o registro no banco |
| **Fluxos Alternativos** | F1. Usuário tenta editar um feedback anônimo → Sistema bloqueia ação e exibe mensagem “Feedback anônimo não pode ser editado” <br> F2. Dados inválidos → Sistema exibe erro |
| **Pós-condições**| 1. O feedback é atualizado com sucesso |
| **Regras de negócio** | 1. Apenas usuários autenticados (Administrador e Colaborador) podem visualizar os feedbacks correspondentes ao seu nível de permissão. <br> 2. O sistema deve garantir que usuários comuns (Colaboradores) só visualizem feedbacks associados a si mesmos.<br> 3. Feedbacks anônimos não podem ser editados <br> 4. Toda edição deve ser registrada no log de auditoria (data, hora e usuário) |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Excluir Feedback  |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador já está autenticado no sistema. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema <br> 2. Sistema valida credenciais <br> 3. Sistema libera acesso <br> 4. Administrador acessa o menu “Feedbacks” no canto superior esquerdo <br> 5. Sistema exibe a lista de feedbacks cadastrados <br> 6. Administrador seleciona um feedback <br> 7. Clica no botão “Excluir” <br> 8. Sistema exibe mensagem de confirmação “Deseja realmente excluir este feedback?” <br> 9. Usuário confirma exclusão <br> 10. Sistema remove o feedback do banco e exibe mensagem “Feedback excluído com sucesso” |
| **Fluxos Alternativos** | F1. Usuário cancela exclusão → Sistema mantém o feedback <br> F2. Feedback não encontrado → Sistema exibe erro |
| **Pós-condições**| 1. O feedback é removido do sistema |
| **Regras de negócio** | 1. Apenas usuários autenticados (Administrador) podem excluir feedbacks anônimos ou feedbacks comuns <br> 2. A exclusão é definitiva e deve ser registrada no log de auditoria <br>  3. Um feedback excluído não pode ser recuperado |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Criar Situação Reportada  |
| **Ator Principal**    | Psicólogo |
| **Pré-condições**     | 1. O psicólogo já está autenticado no sistema. <br> 2. Devem existir colaboradores cadastrados para associação da situação reportada. |
| **Fluxo Principal**   | 1. Psicólogo acessa o sistema. <br> 2. O sistema valida as credenciais. <br> 3. O sistema libera o acesso ao painel principal. <br> 4. O psicólogo acessa o menu “Situações Reportadas” no canto lateral esquerdo. <br> 5. O sistema exibe a tela de gerenciamento de situações reportadas. <br> 6. O psicólogo clica em “Nova Situação”. <br> 7. O sistema exibe o formulário de cadastro com os campos obrigatórios: Colaborador envolvido, Título da situação, Descrição detalhada, Categoria (ex.: conflito, estresse, assédio, etc.) e Data do ocorrido. <br> 8. O psicólogo preenche todos os campos e clica em “Salvar”. <br> 9. O sistema valida os dados informados. <br> 10. O sistema salva a situação reportada no banco de dados e exibe a mensagem “Situação reportada cadastrada com sucesso.” |
| **Fluxos Alternativos** | 1. Dados obrigatórios não preenchidos → O sistema exibe a mensagem “Preencha todos os campos obrigatórios.” <br> 2. Erro de conexão → O sistema exibe a mensagem “Erro ao salvar. Tente novamente mais tarde.” |
| **Pós-condições**| 1. A nova situação reportada é registrada no sistema e associada ao colaborador correspondente. |
| **Regras de negócio** | 1. Todos os campos obrigatórios devem ser preenchidos antes de salvar. <br> 2. O psicólogo deve vincular a situação a um colaborador existente. <br> 3. A data do ocorrido não pode ser futura. <br> 4. O sistema deve registrar data, hora e autor do cadastro no log de auditoria. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Consultar Situação Reportada  |
| **Ator Principal**    | Psicólogo |
| **Pré-condições**     | 1. O psicólogo já está autenticado no sistema. <br> 2.Devem existir situações reportadas cadastradas. |
| **Fluxo Principal**   | 1. O psicólogo acessa o sistema. <br> 2. O sistema valida as credenciais. <br> 3. O sistema libera acesso ao painel principal. <br> 4. O psicólogo acessa o menu “Situações Reportadas”no canto superior esquerdo <br> 5. O sistema exibe a lista de situações reportadas com colunas: Título, Colaborador, Categoria, Data do Ocorrido <br> 6. O psicólogo pode utilizar a barra de busca ou filtros (por colaborador, categoria, período, status). <br> 7. O sistema atualiza a lista conforme os filtros aplicados. <br> 8. O psicólogo seleciona uma situação para visualizar. <br> 9. O sistema exibe uma tela/modal detalhada com todas as informações da situação reportada. |
| **Fluxos Alternativos** | 1. Nenhuma situação encontrada → O sistema exibe a mensagem “Nenhum resultado encontrado.” <br> 2. Falha de conexão → O sistema exibe a mensagem “Erro de conexão. Tente novamente.” |
| **Pós-condições**| 1. O psicólogo visualiza as informações completas da situação selecionada. |
| **Regras de negócio** | 1. A consulta deve permitir filtros múltiplos (colaborador, categoria, período, status). <br> 2. O sistema deve garantir que apenas psicólogos autenticados possam visualizar todas as situações. <br> 3. Consultas devem ser registradas em log para auditoria. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Editar Situação Reportada  |
| **Ator Principal**    | Psicólogo |
| **Pré-condições**     | 1. O psicólogo já está autenticado no sistema. <br> 2.Devem existir situações reportadas cadastradas. |
| **Fluxo Principal**   | 1. O psicólogo acessa o sistema. <br> 2. O sistema valida as credenciais. <br> 3. O sistema libera acesso ao painel principal. <br> 4. O psicólogo acessa o menu “Situações Reportadas”no canto superior esquerdo <br> 5. O sistema exibe a lista de situações existentes. <br> 6. O psicólogo seleciona uma situação e clica em “Editar”. <br> 7. O sistema exibe o formulário com os dados preenchidos. <br> 8. O psicólogo realiza as alterações necessárias (descrição, categoria, status, data do ocorrido, etc.). <br> 9. O psicólogo clica em “Salvar Alterações”. <br> 10. O sistema valida as informações e atualiza o registro, exibindo a mensagem “Situação atualizada com sucesso.” |
| **Fluxos Alternativos** | 1. Campos obrigatórios não preenchidos → Sistema exibe “Preencha todos os campos obrigatórios.” <br> 2. Falha na atualização → Sistema exibe “Erro ao salvar alterações. Tente novamente.” |
| **Pós-condições**| 1. A situação reportada é atualizada no sistema com as novas informações. |
| **Regras de negócio** | 1. O psicólogo não pode alterar o colaborador vinculado à situação. <br> 2. Toda alteração deve ser registrada em log de auditoria (data, hora e responsável). <br> 3. A data do ocorrido não pode ser alterada para uma data futura. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Excluir Situação Reportada  |
| **Ator Principal**    | Psicólogo |
| **Pré-condições**     | 1. O psicólogo já está autenticado no sistema. <br> 2.Devem existir situações reportadas cadastradas. |
| **Fluxo Principal**   | 1. O psicólogo acessa o sistema. <br> 2. O sistema valida as credenciais. <br> 3. O sistema libera acesso ao painel principal. <br> 4. O psicólogo acessa o menu “Situações Reportadas” no canto superior esquerdo <br> 5. O sistema exibe a lista de situações cadastradas. <br> 6. O psicólogo seleciona uma situação e clica em “Excluir”. <br> 7. O sistema exibe uma mensagem de confirmação: “Deseja realmente excluir esta situação reportada?” <br> 8. O psicólogo confirma a exclusão. <br> 9. O sistema remove o registro do banco de dados e exibe a mensagem “Situação reportada excluída com sucesso.” |
| **Fluxos Alternativos** | 1. Psicólogo cancela a exclusão → O sistema mantém a situação ativa. <br> 2. Erro de exclusão (falha de conexão ou restrição de integridade) → Sistema exibe “Não foi possível excluir. Tente novamente mais tarde.” |
| **Pós-condições**| 1. Psicólogo cancela a exclusão → O sistema mantém a situação ativa. <br> 2. Erro de exclusão (falha de conexão ou restrição de integridade) → Sistema exibe “Não foi possível excluir. Tente novamente mais tarde.” |
| **Regras de negócio** | 1. Apenas psicólogos autenticados podem excluir situações. <br> 2. Situações vinculadas a relatórios não podem ser excluídas. <br> 3. Toda exclusão deve ser registrada no log de auditoria (data, hora e usuário responsável). |



| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Acessar dashboard  |
| **Ator Principal**    | Psicólogo, Gestor da Equipe |
| **Pré-condições**     | 1. Ator principal já autenticado no sistema. |
| **Fluxo Principal**   | 1. O ator principal acessa o sistema. <br> 2. O sistema valida as credenciais. <br> 3. O sistema libera acesso ao painel principal. <br> 4. O ator principal clica no botão “Acessar Dashboard”no canto superior esquerdo <br> 5. O sistema exibe a página do dashboard mostrando análise feita a partir da média das questões no banco de dados dos questionários respondido. |
| **Fluxos Alternativos** | 1. Questionários não respondidos. → Aparece mensagem "Sem informações" |
| **Pós-condições**| 1. O sistema exibe dashboard com análise dos questionários respondidos. |
| **Regras de negócio** | 1. Apenas o psicólogo e o gestor da equipe podem acessar o dashboard. |

| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Responder questionário |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | 1. Ator principal na tela questionário. |
| **Fluxo Principal**   | 1. Usuário acessa o painel principal do sistema. <br> 2. O sistema valida as credenciais e libera acesso ao menu lateral. <br> 3. O usuário acessa o menu “Questionário”, localizado no canto lateral esquerdo da tela. <br> 4. O sistema exibe a tela  com o questionário disponível, apresentando sua lista de questões. <br> 5. O ator principal preenche os campos editáveis do questionário, escolhendo uma nota de 1 a 10 da escala likert. |
| **Regras de negócio** | 1. Apenas o colaborador pode responder o questionário. |

| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Enviar questionário |
| **Ator Principal**    | Colaborador |
| **Pré-condições**     | 1. Ator principal já autenticado no sistema. |
| **Fluxo Principal**   | 1. O ator principal acessa o sistema. <br> 2. O sistema valida as credenciais. <br> 3. O sistema libera acesso ao painel principal. <br> 4. O ator principal clica no botão “Enviar questionário” no centro inferior da página. |
| **Fluxos Alternativos** | 1. Campos obrigatórios não preenchidos → Sistema exibe um asterisco (*) vermelho ao lado da questão não preenchida e exibe a mensagem “Preencha todos os campos obrigatórios.” |
| **Pós-condições**| 1. O sistema salva o questionário respondido no seu banco de dados. |
| **Regras de negócio** | 1. Todos os campos obrigatórios devem ser preenchidos antes de enviar o questionário. |


| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Enviar Feedback |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador deve estar autenticado no sistema. <br> 2. Deve existir um colaborador ou equipe cadastrada para receber o feedback. |
| **Fluxo Principal**   | 1. Administrador acessa o sistema. <br> 2. Sistema valida credenciais. <br> 3. Sistema libera acesso ao painel principal. <br> 4. Administrador acessa o menu “Feedbacks” localizado no canto superior esquerdo. <br> 5. Sistema exibe a tela de gerenciamento de feedbacks. <br> 6. Administrador clica no botão “Novo Feedback”. <br> 7. Sistema exibe o formulário de envio de feedback. <br> 8. Administrador preenche os campos obrigatórios: Título, Destinatário (Colaborador/Equipe), Categoria (Desempenho, Comunicação, Ambiente, etc.), e Descrição. <br> 9. Administrador clica em “Enviar”. <br> 10. Sistema valida os dados e executa o caso de uso <<include>> Responder Feedback, registrando o envio e disponibilizando o feedback ao destinatário. |
| **Fluxos Alternativos** | 1. Dados obrigatórios não preenchidos → Sistema exibe mensagem “Preencha todos os campos obrigatórios.” <br> 2. Erro de conexão → Sistema exibe mensagem “Falha ao enviar feedback. Tente novamente.” |
| **Pós-condições**| O feedback é registrado no sistema, associado ao destinatário e visível na tela de histórico de feedbacks. |
| **Regras de negócio** | 1. Apenas colaboradores autenticados podem enviar feedbacks. <br> 2. O sistema deve registrar a data, hora e o colaborador vinculado <br> 3. O caso de uso inclui (<<include>>) o caso “Responder Feedback”. <br> 4. Feedbacks anônimos não devem exibir informações de identificação do remetente, conforme LGPD. <br> 5. Apenas Colaboradores e Gestores de Equipe podem responder os feedbacks. |

| Item                  | Descrição |
|-----------------------|-----------|
| **Nome**              | Responder Feedback |
| **Ator Principal**    | Administrador |
| **Pré-condições**     | 1. O administrador e colaborador devem estar autenticados no sistema. <br> 2. Deve existir um feedback recebido e ativo aguardando resposta |
| **Fluxo Principal**   | 1. Colaborador acessa o sistema. <br> 2. Sistema valida credenciais e libera acesso <br> 3. Colaborador acessa o menu “Meus Feedbacks” no canto superior esquerdo <br> 4. Sistema exibe a lista de feedbacks recebidos. <br> 5. Colaborador seleciona um feedback para visualizar. <br> 6. Sistema exibe os detalhes do feedback (Título, Categoria, Data, Conteúdo e Remetente — se identificado). <br> 7. Colaborador clica no botão “Responder”. <br> 8. Sistema exibe um campo de texto para inserção da resposta. <br> 9. Colaborador digita a resposta e confirma clicando em “Enviar Resposta”. <br> 10. Sistema registra a resposta, vincula ao feedback original e notifica o administrador responsável. |
| **Fluxos Alternativos** | 1. Feedback já respondido → Sistema exibe mensagem “Este feedback já foi respondido.” <br> 2. Erro ao enviar → Sistema exibe mensagem “Falha ao registrar a resposta. Tente novamente.” |
| **Pós-condições**| 1. A resposta é registrada com sucesso, vinculada ao feedback original e armazenada no histórico. <br> 2. Sistema envia resposta ao colaborador vinculado ao feedback. |
| **Regras de negócio** | 1. Cada feedback pode receber apenas uma resposta por colaborador. <br> 2. O sistema deve registrar data, hora colaborador vinculado. <br> 3. Feedbacks anônimos devem manter a privacidade do remetente. <br> 4. Este caso de uso é incluído (<<include>>) em “Enviar Feedback”. |




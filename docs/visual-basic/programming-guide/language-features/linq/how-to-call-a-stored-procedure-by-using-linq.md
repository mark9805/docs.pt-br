---
title: 'Como: chamar um procedimento armazenado usando o LINQ'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: f91ccda1842887b3785ce304fd41bdd020a55479
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345022"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>Como chamar um procedimento armazenado usando LINQ (Visual Basic)
A consulta integrada à linguagem (LINQ) facilita o acesso a informações do banco de dados, incluindo objetos de banco de dados, como procedimentos armazenados.  
  
 O exemplo a seguir mostra como criar um aplicativo que chama um procedimento armazenado em um banco de dados SQL Server. O exemplo mostra como chamar dois procedimentos armazenados diferentes no banco de dados. Cada procedimento retorna os resultados de uma consulta. Um procedimento usa parâmetros de entrada e o outro procedimento não usa parâmetros.  
  
 Os exemplos neste tópico usam o banco de dados de exemplo Northwind. Caso não tenha esse banco de dados no seu computador de desenvolvimento, você poderá baixá-lo no Centro de Download da Microsoft. Para obter instruções, consulte [baixar bancos de dados de exemplo](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>Para criar uma conexão com um banco de dados  
  
1. No Visual Studio, abra **Gerenciador de Servidores**/**Gerenciador de Banco de Dados** clicando em **Gerenciador de servidores**/**Gerenciador de banco de dados** no menu **Exibir** .  
  
2. Clique com o botão direito do mouse em **conexões de dados** no **Gerenciador de servidores**/**Gerenciador de banco de dados** e clique em **Adicionar conexão**.  
  
3. Especifique uma conexão válida para o banco de dados de exemplo Northwind.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>Para adicionar um projeto que contém um arquivo de LINQ to SQL  
  
1. No Visual Studio, no menu **Arquivo**, aponte para **Novo** e clique em **Projeto**. Selecione Visual Basic **aplicativo Windows Forms** como o tipo de projeto.  
  
2. No menu **Projeto**, clique em **Adicionar Novo Item**. Selecione o modelo de item **classes de LINQ to SQL** .  
  
3. Dê o nome `northwind.dbml` para o arquivo. Clique em **Adicionar**. O Object Relational Designer (O/R Designer) é aberto para o arquivo Northwind. dbml.  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>Para adicionar procedimentos armazenados ao o/R Designer  
  
1. Em **Gerenciador de Servidores**/**Gerenciador de banco de dados**, expanda a conexão com o banco de dados Northwind. Expanda a pasta **procedimentos armazenados** .  
  
     Se você fechou o o/R Designer, você pode reabri-lo clicando duas vezes no arquivo Northwind. dbml que você adicionou anteriormente.  
  
2. Clique no procedimento armazenado **vendas por ano** e arraste-o para o painel direito do designer. Clique no procedimento armazenado **dez produtos mais caros** arraste-o para o painel direito do designer.  
  
3. Salve as alterações e feche o designer.  
  
4. Salve seu projeto.  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>Para adicionar código para exibir os resultados dos procedimentos armazenados  
  
1. Na **caixa de ferramentas**, arraste um controle de <xref:System.Windows.Forms.DataGridView> para o formulário padrão do Windows para seu projeto, Form1.  
  
2. Clique duas vezes em Form1 para adicionar código ao seu evento de `Load`.  
  
3. Quando você adicionou procedimentos armazenados ao o/R Designer, o designer adicionou um objeto de <xref:System.Data.Linq.DataContext> para seu projeto. Esse objeto contém o código que você deve ter para acessar esses procedimentos. O objeto <xref:System.Data.Linq.DataContext> para o projeto é nomeado com base no nome do arquivo. dbml. Para este projeto, o objeto <xref:System.Data.Linq.DataContext> é nomeado `northwindDataContext`.  
  
     Você pode criar uma instância do <xref:System.Data.Linq.DataContext> em seu código e chamar os métodos de procedimento armazenado especificados pelo o/R Designer. Para associar ao objeto <xref:System.Windows.Forms.DataGridView>, talvez seja necessário forçar a execução imediata da consulta chamando o método <xref:System.Linq.Enumerable.ToList%2A> nos resultados do procedimento armazenado.  
  
     Adicione o seguinte código ao evento `Load` para chamar qualquer um dos procedimentos armazenados expostos como métodos para seu contexto de dados.  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4. Pressione F5 para executar o projeto e exibir os resultados.  
  
## <a name="see-also"></a>Consulte também

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [Consultas](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Métodos DataContext (Designer Relacional de Objetos)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [Como atribuir procedimentos armazenados para executar atualizações, inserções e exclusões (Designer Relacional de Objetos)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)

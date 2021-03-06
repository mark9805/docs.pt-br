---
title: Como estender o namespace My
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 2a7b0b84061fccd9a333a68e4a19477bd19ca4ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74330308"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Estendendo o namespace `My` no Visual Basic

O namespace `My` no Visual Basic expõe propriedades e métodos que permitem que você aproveite facilmente o poder da .NET Framework. O namespace `My` simplifica problemas comuns de programação, reduzindo muitas vezes uma tarefa difícil para uma única linha de código. Além disso, o namespace `My` é totalmente extensível para que você possa personalizar o comportamento de `My` e adicionar novos serviços à sua hierarquia para se adaptar às necessidades específicas do aplicativo. Este tópico discute como personalizar Membros existentes do namespace `My` e como adicionar suas próprias classes personalizadas ao namespace `My`.

## <a name="customizing-existing-my-namespace-members"></a>Personalizando membros do namespace de `My` existente

O namespace `My` no Visual Basic expõe informações usadas com frequência sobre seu aplicativo, seu computador e muito mais. Para obter uma lista completa dos objetos no namespace `My`, consulte [minha referência](../../language-reference/keywords/my-reference.md). Talvez seja necessário personalizar os membros existentes do namespace `My` para que eles correspondam melhor às necessidades do seu aplicativo. Qualquer propriedade de um objeto no namespace `My` que não seja somente leitura pode ser definida como um valor personalizado.

Por exemplo, suponha que você use frequentemente o objeto `My.User` para acessar o contexto de segurança atual para o usuário que está executando seu aplicativo. No entanto, sua empresa usa um objeto de usuário personalizado para expor informações adicionais e recursos para usuários dentro da empresa. Nesse cenário, você pode substituir o valor padrão da propriedade `My.User.CurrentPrincipal` por uma instância do seu próprio objeto principal personalizado, conforme mostrado no exemplo a seguir:

[!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]

Definir a propriedade `CurrentPrincipal` no objeto `My.User` altera a identidade sob a qual o aplicativo é executado. O objeto `My.User`, por sua vez, retorna informações sobre o usuário especificado recentemente.
  
## <a name="adding-members-to-my-objects"></a>Adicionando membros a objetos `My`

Os tipos retornados de `My.Application` e `My.Computer` são definidos como classes `Partial`. Portanto, você pode estender os objetos `My.Application` e `My.Computer` criando uma classe `Partial` chamada `MyApplication` ou `MyComputer`. A classe não pode ser uma classe `Private`. Se você especificar a classe como parte do namespace `My`, poderá adicionar propriedades e métodos que serão incluídos com os objetos `My.Application` ou `My.Computer`.

O exemplo a seguir adiciona uma propriedade chamada `DnsServerIPAddresses` ao objeto `My.Computer`:

[!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]

## <a name="adding-custom-objects-to-the-my-namespace"></a>Adicionando objetos personalizados ao namespace `My`

Embora o namespace `My` forneça soluções para muitas tarefas comuns de programação, você pode encontrar tarefas que o namespace de `My` não resolve. Por exemplo, seu aplicativo pode acessar serviços de diretório personalizados para dados de usuário ou seu aplicativo pode usar assemblies que não são instalados por padrão com Visual Basic. Você pode estender o namespace `My` para incluir soluções personalizadas para tarefas comuns que são específicas para seu ambiente. O namespace `My` pode ser estendido facilmente para adicionar novos membros para atender às necessidades crescentes do aplicativo. Além disso, você pode implantar suas extensões de namespace `My` para outros desenvolvedores como um modelo de Visual Basic.
  
### <a name="adding-members-to-the-my-namespace"></a>Adicionando Membros ao namespace `My`

Como `My` é um namespace como qualquer outro namespace, você pode adicionar propriedades de nível superior a ele apenas adicionando um módulo e especificando uma `Namespace` de `My`. Anote o módulo com o atributo `HideModuleName`, conforme mostrado no exemplo a seguir. O atributo `HideModuleName` garante que o IntelliSense não exibirá o nome do módulo quando ele exibir os membros do namespace `My`.

[!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]

Para adicionar membros ao namespace `My`, adicione propriedades conforme necessário ao módulo. Para cada propriedade adicionada ao namespace `My`, adicione um campo particular do tipo `ThreadSafeObjectProvider(Of T)`, em que o tipo é o tipo retornado por sua propriedade personalizada. Esse campo é usado para criar instâncias de objeto thread-safe a serem retornadas pela propriedade chamando o método `GetInstance`. Como resultado, cada thread que está acessando a propriedade estendida recebe sua própria instância do tipo retornado. O exemplo a seguir adiciona uma propriedade chamada `SampleExtension` que é do tipo `SampleExtension` ao namespace `My`:

[!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]

## <a name="adding-events-to-custom-my-objects"></a>Adicionando eventos a objetos de `My` personalizados

Você pode usar o objeto `My.Application` para expor eventos para seus objetos de `My` personalizados, estendendo a classe parcial `MyApplication` no namespace `My`. Para projetos baseados no Windows, você pode clicar duas vezes no nó **meu projeto** no para seu projeto no **Gerenciador de soluções**. No Visual Basic **Designer de projeto**, clique na guia **aplicativo** e, em seguida, clique no botão **Exibir eventos de aplicativo** . Um novo arquivo chamado *ApplicationEvents. vb* será criado. Ele contém o código a seguir para estender a classe `MyApplication`:

[!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]

Você pode adicionar manipuladores de eventos para seus objetos de `My` personalizados adicionando manipuladores de eventos personalizados à classe `MyApplication`. Os eventos personalizados permitem que você adicione o código que será executado quando um manipulador de eventos for adicionado, removido ou o evento for gerado. Observe que o código de `AddHandler` para um evento personalizado será executado somente se o código for adicionado por um usuário para manipular o evento. Por exemplo, considere que o objeto `SampleExtension` da seção anterior tem um evento `Load` ao qual você deseja adicionar um manipulador de eventos personalizado. O exemplo de código a seguir mostra um manipulador de eventos personalizado chamado `SampleExtensionLoad` que será invocado quando o evento de `My.SampleExtension.Load` ocorrer. Quando o código é adicionado para manipular o novo evento `My.SampleExtensionLoad`, a parte `AddHandler` desse código de evento personalizado é executada. O método `MyApplication_SampleExtensionLoad` é incluído no exemplo de código para mostrar um exemplo de um manipulador de eventos que manipula o evento `My.SampleExtensionLoad`. Observe que o evento `SampleExtensionLoad` estará disponível quando você selecionar a opção **meus eventos de aplicativo** na lista suspensa à esquerda acima do editor de código ao editar o arquivo *ApplicationEvents. vb* .

[!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]

## <a name="design-guidelines"></a>Diretrizes de design

Ao desenvolver extensões para o namespace `My`, use as diretrizes a seguir para ajudar a minimizar os custos de manutenção de seus componentes de extensão:

- **Inclua apenas a lógica de extensão.** A lógica incluída na extensão do namespace `My` deve incluir apenas o código necessário para expor a funcionalidade necessária no namespace `My`. Como sua extensão residirá em projetos de usuário como código-fonte, a atualização do componente de extensão incorrerá em um custo de manutenção alto e deverá ser evitada, se possível.
- **Minimize as suposições do projeto.** Quando você cria suas extensões do namespace `My`, não presuma um conjunto de referências, importações no nível do projeto ou configurações específicas do compilador (por exemplo, `Option Strict` desativado). Em vez disso, minimize as dependências e qualifique totalmente todas as referências de tipo usando a palavra-chave `Global`. Além disso, certifique-se de que a extensão seja compilada com `Option Strict` para minimizar erros na extensão.
- **Isole o código de extensão.** Colocar o código em um único arquivo torna sua extensão facilmente implantável como um modelo de item do Visual Studio. Para obter mais informações, consulte "empacotando e implantando extensões", mais adiante neste tópico. Colocar todos os `My` código de extensão de namespace em um único arquivo ou em uma pasta separada em um projeto também ajudará os usuários a localizar a extensão de namespace de `My`.

## <a name="designing-class-libraries-for-my"></a>Criando bibliotecas de classes para `My`

Como é o caso da maioria dos modelos de objeto, alguns padrões de design funcionam bem no namespace `My` e outros não. Ao criar uma extensão para o namespace `My`, considere os seguintes princípios:

- **Métodos sem estado.** Os métodos no namespace `My` devem fornecer uma solução completa para uma tarefa específica. Certifique-se de que os valores de parâmetro que são passados para o método forneçam toda a entrada necessária para concluir a tarefa específica. Evite criar métodos que dependem do estado anterior, como conexões abertas para recursos.
- **Instâncias globais.** O único Estado que é mantido no namespace de `My` é global para o projeto. Por exemplo, `My.Application.Info` encapsula o estado que é compartilhado em todo o aplicativo.
- **Tipos de parâmetro simples.** Mantenha as coisas simples, evitando tipos complexos de parâmetros. Em vez disso, crie métodos que não usam nenhuma entrada de parâmetro ou que usam tipos de entrada simples, como cadeias de caracteres, tipos primitivos e assim por diante.
- **Métodos de fábrica.** Alguns tipos são necessariamente difíceis de instanciar. Fornecer métodos de fábrica como extensões para o namespace `My` permite que você descubra e consuma com mais facilidade os tipos que se enquadram nessa categoria. Um exemplo de um método de fábrica que funciona bem é `My.Computer.FileSystem.OpenTextFileReader`. Há vários tipos de fluxo disponíveis no .NET Framework. Ao especificar arquivos de texto especificamente, o `OpenTextFileReader` ajuda o usuário a entender qual fluxo usar.

Essas diretrizes não impedem princípios gerais de design para bibliotecas de classes. Em vez disso, são recomendações otimizadas para os desenvolvedores que estão usando Visual Basic e o namespace `My`. Para princípios de design gerais para a criação de bibliotecas de classes, consulte [diretrizes de design de estrutura](../../../standard/design-guidelines/index.md).

## <a name="packaging-and-deploying-extensions"></a>Empacotando e implantando extensões

Você pode incluir `My` extensões de namespace em um modelo de projeto do Visual Studio ou pode empacotar suas extensões e implantá-las como um modelo de item do Visual Studio. Ao empacotar suas extensões de namespace `My` como um modelo de item do Visual Studio, você pode aproveitar os recursos adicionais fornecidos pelo Visual Basic. Esses recursos permitem que você inclua uma extensão quando um projeto faz referência a um determinado assembly ou permite que os usuários adicionem explicitamente sua extensão de namespace de `My` usando a página **minhas extensões** do designer de projeto Visual Basic.

Para obter detalhes sobre como implantar `My` extensões de namespace, consulte [empacotando e implantando minhas extensões personalizadas](packaging-and-deploying-custom-my-extensions.md).

## <a name="see-also"></a>Consulte também

- [Empacotando e implantando minhas extensões personalizadas](packaging-and-deploying-custom-my-extensions.md)
- [Estendendo o modelo de aplicativo do Visual Basic](extending-the-visual-basic-application-model.md)
- [Personalizando quais objetos estão disponíveis em My](customizing-which-objects-are-available-in-my.md)
- [Página Minhas extensões, Designer de Projeto](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [Página de Aplicativo, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Parcial](../../language-reference/modifiers/partial.md)

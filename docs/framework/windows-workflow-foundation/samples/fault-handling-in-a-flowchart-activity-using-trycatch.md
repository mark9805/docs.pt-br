---
title: Tratamento de falha em uma atividade do fluxograma usando TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710832"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Tratamento de falha em uma atividade do fluxograma usando TryCatch

Este exemplo mostra como a atividade de <xref:System.Activities.Statements.TryCatch> pode ser usada dentro de uma atividade complexa de fluxo de controle.

Nesse exemplo, um código da promoção e um número de filhos são passados como variáveis a uma atividade de <xref:System.Activities.Statements.Flowchart> que calcula desconto com base nas fórmulas que correspondem ao código da promoção. O exemplo inclui versões imperativas do designer de código e de fluxo de trabalho de exemplo.

A tabela a seguir detalha as variáveis para atividades de `CreateFlowchartWithFaults` .

|Parâmetros|Descrição|
|----------------|-----------------|
|promoCode|O código da promoção. Tipo: String<br /><br /> Os valores possíveis com descrição entre parênteses:<br /><br /> -Único (único)<br />-MNK (casado sem crianças).<br />-MWK (casado com filhos).|
|numKids|O número de filho. Tipo: int|

A atividade de `CreateFlowchartWithFaults` usa uma atividade de <xref:System.Activities.Statements.FlowSwitch%601> que alterna no argumento de `promoCode` e calculem o desconto usando a fórmula seguir.

|Valor de `promoCode`|Desconto (%)|
|--------------------------|--------------------|
|Simples|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Observação:** potencialmente, esse cálculo pode lançar uma <xref:System.DivideByZeroException>. Assim, o cálculo de desconto é empacotado em uma atividade de <xref:System.Activities.Statements.TryCatch> que captura a exceção de <xref:System.DivideByZeroException> e defina o desconto a zero.|

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2010, abra o arquivo de solução FlowchartWithFaultHandling. sln.

2. Para criar a solução, pressione CTRL+SHIFT+B.

3. Para executar a solução, pressione F5.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Consulte também

- [Fluxos de trabalho de fluxograma](../flowchart-workflows.md)
- [Exceções](../exceptions.md)

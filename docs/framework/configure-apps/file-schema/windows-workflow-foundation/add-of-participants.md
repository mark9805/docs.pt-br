---
title: <add> de <participants>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c730850-6f8e-4102-acb8-8effb4e09463
ms.openlocfilehash: 61832edbf7d206d6a5f7a85619eb17ebc010c193
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152353"
---
# <a name="add-of-participants"></a>\<adicionar> \<de participantes>
Configure um participante de rastreamento que escuta para registros de rastreamento emissores de runtime diretamente e processá-los de forma que ele foi configurado. Isso inclui a escrita em uma saída específica (por exemplo, arquivo, Console, ETW), processamento/agregando os registros ou qualquer outra combinação que pode ser necessária.  
  
 Para obter mais informações sobre os participantes de rastreamento e rastreamento do fluxo [de trabalho,](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) consulte [Participantes](../../../windows-workflow-foundation/tracking-participants.md)de rastreamento e rastreamento de fluxo de trabalho .  
  
[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<Sistema.>de modelo de serviço**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<rastreando>**](tracking.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<participantes>**](participants.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<tracking>
  <participants>
    <add name="String" profileName="String" type="String" />
  </participants>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|name|Uma cadeia de caracteres que especifica o nome de um participante de rastreamento.|  
|profileName|Uma cadeia de caracteres que especifica o nome do perfil de rastreamento que define os registros de rastreamento o participante de rastreamento tiver assinado.|  
|type|Uma cadeia de caracteres que especifica o tipo de um participante de rastreamento.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<participantes>](participants.md)|Uma lista de participantes de rastreamento|  
  
## <a name="remarks"></a>Comentários  
 Os participantes de rastreamento são usados para obter os dados de rastreamento emissores de fluxo de trabalho e armazená-lo em mídias diferentes. Da mesma forma, qualquer pós-processamento no controle de que registros também podem ser realizados o participante de rastreamento.  
  
 Vários participantes de rastreamento podem consumir os eventos de rastreamento simultaneamente. Cada participante de rastreamento pode ser associado um perfil de controle diferentes.  
  
 Um participante de rastreamento padrão é fornecido, que grava os registros de rastreamento em uma sessão do ETW. O participante é configurado em um serviço de fluxo de trabalho adicionando um comportamento acompanhamento- específico em um arquivo de configuração. Ativar um participante de rastreamento de ETW permite controlar os registros a serem exibidos no visualizador de eventos. Se isso não atender aos requisitos, você também poderá escrever um participante de rastreamento personalizado.  
  
## <a name="example"></a>Exemplo  
 O exemplo de configuração a seguir mostra o participante de rastreamento ETW padrão que está sendo configurado no arquivo Web. config.  
  
 O ID do Provedor que o Participante de Rastreamento do ETW ** \<** usa para escrever os Registros de Rastreamento para ETW é definido na seção de diagnósticos>. O participante de rastreamento tem um perfil associado a ele para especificar os registros de rastreamento que tiver assinado. Isso é definido pelo atributo **profileName** do ** \<** elemento add>. Uma vez definidos, o Participante de rastreamento é adicionado ao ** \<etwTracking>** comportamento de serviço. Isso adicionará os participantes de rastreamento selecionado para extensões da instância de fluxo de trabalho, para que eles começam a receber os registros de rastreamento.  
  
```xml  
<configuration>
  <system.web>
    <compilation targetFrameworkMoniker=".NETFramework,Version=v4.0"/>
  </system.web>
  <system.serviceModel>
    <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />
    <tracking>
      <participants>
        <add name="EtwTrackingParticipant"
             type="System.Activities.Tracking.EtwTrackingParticipant, System.Activities, Version=4.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
             profileName="HealthMonitoring_Tracking_Profile"/>
      </participants>
    </tracking>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.ServiceModel.Activities.Tracking.Configuration.TrackingSection>
- <xref:System.ServiceModel.Activities.Description.EtwTrackingBehavior>
- <xref:System.ServiceModel.Activities.Configuration.EtwTrackingBehaviorElement>
- [Acompanhamento e rastreamento de fluxo de trabalho](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [Acompanhando participantes](../../../windows-workflow-foundation/tracking-participants.md)

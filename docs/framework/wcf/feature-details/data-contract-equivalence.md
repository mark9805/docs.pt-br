---
title: Equivalência de contrato de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], equivalence
ms.assetid: f06f3c7e-c235-4ec1-b200-68142edf1ed1
ms.openlocfilehash: 448c47d8687aa32671ade016f9b48cd763f87dfb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945356"
---
# <a name="data-contract-equivalence"></a>Equivalência de contrato de dados
Para um cliente enviar com êxito dados de um determinado tipo para um serviço, ou um serviço para enviar dados com êxito a um cliente, o tipo enviado não precisa necessariamente existir na extremidade de recebimento. O único requisito é que os contratos de dados de ambos os tipos sejam equivalentes. (Às vezes, a equivalência estrita não é necessária, conforme discutido em [controle de versão de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).)  
  
 Para que os contratos de dados sejam equivalentes, eles devem ter o mesmo namespace e nome. Além disso, cada membro de dados em um lado deve ter um membro de dados equivalente no outro lado.  
  
 Para que os membros de dados sejam equivalentes, eles devem ter o mesmo nome. Além disso, eles devem representar o mesmo tipo de dados; ou seja, seus contratos de dados devem ser equivalentes.  
  
> [!NOTE]
> Observe que os nomes de contrato de dados e namespaces, bem como os nomes de membro de dados, diferenciam maiúsculas de minúsculas.  
  
 Para obter mais informações sobre nomes de contrato de dados e namespaces, bem como nomes de membros de dados, consulte [nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Se dois tipos existirem no mesmo lado (remetente ou destinatário) e seus contratos de dados não forem equivalentes (por exemplo, se tiverem membros de dados diferentes), você não deverá dar a eles o mesmo nome e namespace. Isso pode fazer com que as exceções sejam geradas.  
  
 Os contratos de dados para os seguintes tipos são equivalentes:  
  
 [!code-csharp[C_DataContractNames#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#5)]
 [!code-vb[C_DataContractNames#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#5)]  
  
## <a name="data-member-order-and-data-contract-equivalence"></a>Equivalência do contrato de dados e da ordem do membro de dados  
 O uso <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> da propriedade da <xref:System.Runtime.Serialization.DataMemberAttribute> classe pode afetar a equivalência do contrato de dados. Os contratos de dados devem ter membros que aparecem na mesma ordem para serem equivalentes. A ordem padrão é alfabética. Para obter mais informações, consulte [ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 Por exemplo, o código a seguir resulta em contratos de dados equivalentes.  
  
 [!code-csharp[C_DataContractNames#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#6)]
 [!code-vb[C_DataContractNames#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#6)]  
  
 No entanto, o seguinte não resulta em um contrato de dados equivalente.  
  
 [!code-csharp[C_DataContractNames#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#7)]
 [!code-vb[C_DataContractNames#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#7)]  
  
## <a name="inheritance-interfaces-and-data-contract-equivalence"></a>Herança, interfaces e equivalência de contrato de dados  
 Ao determinar a equivalência, um contrato de dados herdado de outro contrato de dados é tratado como se fosse apenas um contrato de dados que inclui todos os membros de dados do tipo base. Tenha em mente que a ordem dos membros de dados deve corresponder e que os membros do tipo base precedem membros de tipo derivado na ordem. Além disso, se, como no exemplo de código a seguir, dois membros de dados tiverem o mesmo valor de ordem, a ordenação desses membros de dados será alfabética. Para obter mais informações, consulte [ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 No exemplo a seguir, o contrato de dados para `Employee` o tipo é equivalente ao contrato de dados para `Worker`o tipo.  
  
 [!code-csharp[C_DataContractNames#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#8)]
 [!code-vb[C_DataContractNames#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#8)]  
  
 Ao passar parâmetros e retornar valores entre um cliente e um serviço, um contrato de dados de uma classe base não pode ser enviado quando o ponto de extremidade de recebimento espera um contrato de dados de uma classe derivada. Isso é de acordo com as filosofias de programação orientada a objeto. No exemplo anterior, um objeto do tipo `Person` não pode ser enviado quando um `Employee` é esperado.  
  
 Um contrato de dados de uma classe derivada pode ser enviado quando um contrato de dados de uma classe base é esperado, mas somente se o ponto de extremidade de recebimento "souber" do <xref:System.Runtime.Serialization.KnownTypeAttribute>tipo derivado usando o. Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md). No exemplo anterior, um objeto do tipo `Employee` pode ser enviado quando um `Person` é esperado, mas somente se o código do receptor empregar o <xref:System.Runtime.Serialization.KnownTypeAttribute> para incluí-lo na lista de tipos conhecidos.  
  
 Ao passar parâmetros e retornar valores entre aplicativos, se o tipo esperado for uma interface, ele será equivalente ao tipo esperado sendo do tipo <xref:System.Object>. Como todos os tipos derivam de <xref:System.Object>, todos os contratos de dados derivam do contrato de dados <xref:System.Object>para o. Assim, qualquer tipo de contrato de dados pode ser passado quando uma interface é esperada. Etapas adicionais são necessárias para trabalhar com êxito com interfaces; para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- [Ordem de membro de dados](../../../../docs/framework/wcf/feature-details/data-member-order.md)
- [Tipos conhecidos de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Nomes de contrato de dados](../../../../docs/framework/wcf/feature-details/data-contract-names.md)

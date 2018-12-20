---
title: Treinar um modelo de machine learning usando dados que não estão em um arquivo de texto – ML.NET
description: Descubra como usar o ML.NET para carregar dados de treinamento que não estão em um arquivo para o treinamento do modelo de machine learning durante o pipeline de previsão.
ms.date: 11/07/2018
ms.custom: mvc,how-to
ms.openlocfilehash: 971c5c62acc9dd7bf29aa11ce898c2b76822c3d7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125396"
---
# <a name="train-a-machine-learning-model-with-data-thats-not-in-a-text-file---mlnet"></a><span data-ttu-id="d6069-103">Treinar um modelo de machine learning usando dados que não estão em um arquivo de texto – ML.NET</span><span class="sxs-lookup"><span data-stu-id="d6069-103">Train a machine learning model with data that's not in a text file - ML.NET</span></span>

<span data-ttu-id="d6069-104">O caso de uso do ML.NET que normalmente é demonstrado é usar o `TextLoader` para ler os dados de treinamento de um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d6069-104">The commonly demonstrated use case for ML.NET is use the `TextLoader` to read the training data from a file.</span></span>
<span data-ttu-id="d6069-105">No entanto, em cenários de treinamento em tempo real, os dados podem ser obtidos de outra forma, como:</span><span class="sxs-lookup"><span data-stu-id="d6069-105">However, in real-time training scenarios the data can be elsewhere, such as:</span></span>

* <span data-ttu-id="d6069-106">em tabelas SQL</span><span class="sxs-lookup"><span data-stu-id="d6069-106">in SQL tables</span></span>
* <span data-ttu-id="d6069-107">extraídos de arquivos de log</span><span class="sxs-lookup"><span data-stu-id="d6069-107">extracted from log files</span></span>
* <span data-ttu-id="d6069-108">gerados em tempo real</span><span class="sxs-lookup"><span data-stu-id="d6069-108">generated on the fly</span></span>

<span data-ttu-id="d6069-109">Use a [compreensão do esquema](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) para levar um `IEnumerable` em C# existente ao ML.NET como uma `DataView`.</span><span class="sxs-lookup"><span data-stu-id="d6069-109">Use [schema comprehension](https://github.com/dotnet/machinelearning/tree/master/docs/code/SchemaComprehension.md) to bring an existing C# `IEnumerable` into ML.NET as a `DataView`.</span></span>

<span data-ttu-id="d6069-110">Neste exemplo, você criará o modelo de previsão de variação do cliente e extrairá estes recursos do seu sistema de produção:</span><span class="sxs-lookup"><span data-stu-id="d6069-110">For this example, you'll build the customer churn prediction model, and extract the following features from your production system:</span></span>

* <span data-ttu-id="d6069-111">ID do cliente (ignorada pelo modelo)</span><span class="sxs-lookup"><span data-stu-id="d6069-111">Customer ID (ignored by the model)</span></span>
* <span data-ttu-id="d6069-112">Se o cliente variou (o 'rótulo' de destino)</span><span class="sxs-lookup"><span data-stu-id="d6069-112">Whether the customer has churned (the target 'label')</span></span>
* <span data-ttu-id="d6069-113">A 'categoria demográfica' (uma cadeia de caracteres como 'jovens adultos' etc.)</span><span class="sxs-lookup"><span data-stu-id="d6069-113">The 'demographic category' (one string, like 'young adult' etc.)</span></span>
* <span data-ttu-id="d6069-114">O número de visitas nos últimos cinco dias.</span><span class="sxs-lookup"><span data-stu-id="d6069-114">The number of visits from the last 5 days.</span></span>

```csharp
private class CustomerChurnInfo
{
    public string CustomerID { get; set; }
    public bool HasChurned { get; set; }
    public string DemographicCategory { get; set; }
    // Visits during last 5 days, latest to newest.
    [VectorType(5)]
    public float[] LastVisits { get; set; }
}
```

<span data-ttu-id="d6069-115">Carregue esses dados no `DataView` e treine o modelo usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="d6069-115">Load this data into the `DataView` and train the model, using the following code:</span></span>

```csharp
// Create a new context for ML.NET operations. It can be used for exception tracking and logging,
// as a catalog of available operations and as the source of randomness.
var mlContext = new MLContext();

// Step one: read the data as an IDataView.
// Let's assume that 'GetChurnData()' fetches and returns the training data from somewhere.
IEnumerable<CustomerChurnInfo> churnData = GetChurnInfo();

// Turn the data into the ML.NET data view.
// We can use CreateDataView or CreateStreamingDataView, depending on whether 'churnData' is an IList,
// or merely an IEnumerable.
var trainData = mlContext.CreateStreamingDataView(churnData);

// Build the learning pipeline.
// In our case, we will one-hot encode the demographic category, and concatenate that with the number of visits.
// We apply our FastTree binary classifier to predict the 'HasChurned' label.

var pipeline = mlContext.Transforms.Categorical.OneHotEncoding("DemographicCategory")
    .Append(mlContext.Transforms.Concatenate("Features", "DemographicCategory", "LastVisits"))
    .Append(mlContext.BinaryClassification.Trainers.FastTree("HasChurned", "Features", numTrees: 20));

var model = pipeline.Fit(trainData);
```
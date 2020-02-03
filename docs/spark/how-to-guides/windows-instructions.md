---
title: Criar um aplicativo .NET para Apache Spark no Windows
description: Saiba como criar seu .NET para Apache Spark aplicativo no Windows.
ms.date: 01/29/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: e6dec09f7d3e8d478cdcccf9df1c3e72d5f884eb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76928032"
---
# <a name="learn-how-to-build-your-net-for-apache-spark-application-on-windows"></a><span data-ttu-id="1efdc-103">Saiba como criar seu .NET para Apache Spark aplicativo no Windows</span><span class="sxs-lookup"><span data-stu-id="1efdc-103">Learn how to build your .NET for Apache Spark application on Windows</span></span>

<span data-ttu-id="1efdc-104">Este artigo ensina como criar seu .NET para aplicativos Apache Spark no Windows.</span><span class="sxs-lookup"><span data-stu-id="1efdc-104">This article teaches you how to build your .NET for Apache Spark applications on Windows.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1efdc-105">{1&gt;{2&gt;Pré-requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1efdc-105">Prerequisites</span></span>

<span data-ttu-id="1efdc-106">Se você já tiver todos os pré-requisitos a seguir, pule para as etapas de [compilação](#build) .</span><span class="sxs-lookup"><span data-stu-id="1efdc-106">If you already have all of the following prerequisites, skip to the [build](#build) steps.</span></span>

  1. <span data-ttu-id="1efdc-107">Baixar e instalar o **[SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core/2.1)** -a instalação do SDK adicionará o `dotnet` ferramentas ao seu caminho.</span><span class="sxs-lookup"><span data-stu-id="1efdc-107">Download and install the **[.NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/2.1)** - installing the SDK will add the `dotnet` toolchain to your path.</span></span> <span data-ttu-id="1efdc-108">Há suporte para o .NET Core 2,1, 2,2 e 3,1.</span><span class="sxs-lookup"><span data-stu-id="1efdc-108">.NET Core 2.1, 2.2 and 3.1 are supported.</span></span>
  2. <span data-ttu-id="1efdc-109">Instale o **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (versão 16,3 ou posterior).</span><span class="sxs-lookup"><span data-stu-id="1efdc-109">Install **[Visual Studio 2019](https://www.visualstudio.com/downloads/)** (Version 16.3 or later).</span></span> <span data-ttu-id="1efdc-110">A versão da Comunidade é totalmente gratuita.</span><span class="sxs-lookup"><span data-stu-id="1efdc-110">The Community version is completely free.</span></span> <span data-ttu-id="1efdc-111">Ao configurar sua instalação, inclua estes componentes no mínimo:</span><span class="sxs-lookup"><span data-stu-id="1efdc-111">When configuring your installation, include these components at minimum:</span></span>
     * <span data-ttu-id="1efdc-112">Desenvolvimento de área de trabalho do .NET</span><span class="sxs-lookup"><span data-stu-id="1efdc-112">.NET desktop development</span></span>
       * <span data-ttu-id="1efdc-113">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="1efdc-113">All Required Components</span></span>
         * <span data-ttu-id="1efdc-114">Ferramentas de desenvolvimento do .NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="1efdc-114">.NET Framework 4.6.1 Development Tools</span></span>
     * <span data-ttu-id="1efdc-115">Desenvolvimento de plataforma cruzada do .NET Core</span><span class="sxs-lookup"><span data-stu-id="1efdc-115">.NET Core cross-platform development</span></span>
       * <span data-ttu-id="1efdc-116">Todos os componentes necessários</span><span class="sxs-lookup"><span data-stu-id="1efdc-116">All Required Components</span></span>
  3. <span data-ttu-id="1efdc-117">Instale o **[Java 1,8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)** .</span><span class="sxs-lookup"><span data-stu-id="1efdc-117">Install **[Java 1.8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)**.</span></span> 
     - <span data-ttu-id="1efdc-118">Selecione a versão apropriada para seu sistema operacional, por exemplo, JDK-8u201-Windows-x64. exe para o computador com o Win x64.</span><span class="sxs-lookup"><span data-stu-id="1efdc-118">Select the appropriate version for your operating system e.g., jdk-8u201-windows-x64.exe for Win x64 machine.</span></span>
     - <span data-ttu-id="1efdc-119">Instale o usando o instalador e verifique se você consegue executar o `java` de sua linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1efdc-119">Install using the installer and verify you are able to run `java` from your command-line.</span></span>
  4. <span data-ttu-id="1efdc-120">Instale o **[Apache Maven 3.6.0 +](https://maven.apache.org/download.cgi)** .</span><span class="sxs-lookup"><span data-stu-id="1efdc-120">Install **[Apache Maven 3.6.0+](https://maven.apache.org/download.cgi)**.</span></span>
     - <span data-ttu-id="1efdc-121">Baixe o [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span><span class="sxs-lookup"><span data-stu-id="1efdc-121">Download [Apache Maven 3.6.0](http://mirror.metrocast.net/apache/maven/maven-3/3.6.0/binaries/apache-maven-3.6.0-bin.zip).</span></span>
     - <span data-ttu-id="1efdc-122">Extraia para um diretório local, por exemplo, `C:\bin\apache-maven-3.6.0\`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-122">Extract to a local directory e.g., `C:\bin\apache-maven-3.6.0\`.</span></span>
     - <span data-ttu-id="1efdc-123">Adicione o Apache Maven à sua [variável de ambiente path](https://www.java.com/en/download/help/path.xml) , por exemplo, `C:\bin\apache-maven-3.6.0\bin`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-123">Add Apache Maven to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\apache-maven-3.6.0\bin`.</span></span>
     - <span data-ttu-id="1efdc-124">Verifique se você pode executar o `mvn` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1efdc-124">Verify you are able to run `mvn` from your command-line.</span></span>
  5. <span data-ttu-id="1efdc-125">Instale o **[Apache Spark 2.3 +](https://spark.apache.org/downloads.html)** .</span><span class="sxs-lookup"><span data-stu-id="1efdc-125">Install **[Apache Spark 2.3+](https://spark.apache.org/downloads.html)**.</span></span>
     - <span data-ttu-id="1efdc-126">Baixe [Apache Spark 2.3 +](https://spark.apache.org/downloads.html) e extraia-o em uma pasta local (por exemplo, `C:\bin\spark-2.3.2-bin-hadoop2.7\`) usando [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="1efdc-126">Download [Apache Spark 2.3+](https://spark.apache.org/downloads.html) and extract it into a local folder (e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`) using [7-zip](https://www.7-zip.org/).</span></span> <span data-ttu-id="1efdc-127">(As versões do Spark com suporte são 2,3. \*, 2.4.0, 2.4.1, 2.4.3 e 2.4.4)</span><span class="sxs-lookup"><span data-stu-id="1efdc-127">(The supported spark versions are 2.3.\*, 2.4.0, 2.4.1, 2.4.3 and 2.4.4)</span></span>
     - <span data-ttu-id="1efdc-128">Adicione uma [nova variável de ambiente](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` por exemplo, `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-128">Add a [new environment variable](https://www.java.com/en/download/help/path.xml) `SPARK_HOME` e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\`.</span></span>

       ```powershell
       set SPARK_HOME=C:\bin\spark-2.3.2-bin-hadoop2.7\       
       ```

     - <span data-ttu-id="1efdc-129">Adicione Apache Spark à sua [variável de ambiente path](https://www.java.com/en/download/help/path.xml) , por exemplo, `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-129">Add Apache Spark to your [PATH environment variable](https://www.java.com/en/download/help/path.xml) e.g., `C:\bin\spark-2.3.2-bin-hadoop2.7\bin`.</span></span>

       ```powershell       
       set PATH=%SPARK_HOME%\bin;%PATH%
       ```
     
     - <span data-ttu-id="1efdc-130">Verifique se você pode executar o `spark-shell` da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="1efdc-130">Verify you are able to run `spark-shell` from your command-line.</span></span>        
        <span data-ttu-id="1efdc-131">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="1efdc-131">Sample console output:</span></span>

        ```
        Welcome to
              ____              __
             / __/__  ___ _____/ /__
            _\ \/ _ \/ _ `/ __/  '_/
           /___/ .__/\_,_/_/ /_/\_\   version 2.3.2
              /_/

        Using Scala version 2.11.8 (Java HotSpot(TM) 64-Bit Server VM, Java 1.8.0_201)
        Type in expressions to have them evaluated.
        Type :help for more information.

        scala> sc
        res0: org.apache.spark.SparkContext = org.apache.spark.SparkContext@6eaa6b0c
        ```

        </details>

  6. <span data-ttu-id="1efdc-132">Instale o **[WinUtils](https://github.com/steveloughran/winutils)** .</span><span class="sxs-lookup"><span data-stu-id="1efdc-132">Install **[WinUtils](https://github.com/steveloughran/winutils)**.</span></span>
     - <span data-ttu-id="1efdc-133">Baixe `winutils.exe` binário do [repositório WinUtils](https://github.com/steveloughran/winutils).</span><span class="sxs-lookup"><span data-stu-id="1efdc-133">Download `winutils.exe` binary from [WinUtils repository](https://github.com/steveloughran/winutils).</span></span> <span data-ttu-id="1efdc-134">Você deve selecionar a versão do Hadoop com a qual a distribuição do Spark foi compilada, por exemplo, usar Hadoop-2.7.1 para Spark 2.3.2.</span><span class="sxs-lookup"><span data-stu-id="1efdc-134">You should select the version of Hadoop the Spark distribution was compiled with, e.g. use hadoop-2.7.1 for Spark 2.3.2.</span></span>
     - <span data-ttu-id="1efdc-135">Salve `winutils.exe` binário em um diretório de sua escolha, por exemplo, `C:\hadoop\bin`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-135">Save `winutils.exe` binary to a directory of your choice e.g., `C:\hadoop\bin`.</span></span>
     - <span data-ttu-id="1efdc-136">Defina `HADOOP_HOME` para refletir o diretório com winutils. exe (sem bin).</span><span class="sxs-lookup"><span data-stu-id="1efdc-136">Set `HADOOP_HOME` to reflect the directory with winutils.exe (without bin).</span></span> <span data-ttu-id="1efdc-137">Por exemplo, usando a linha de comando:</span><span class="sxs-lookup"><span data-stu-id="1efdc-137">For instance, using command-line:</span></span>

       ```powershell
       set HADOOP_HOME=C:\hadoop
       ```

     - <span data-ttu-id="1efdc-138">Defina a variável de ambiente PATH para incluir `%HADOOP_HOME%\bin`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-138">Set PATH environment variable to include `%HADOOP_HOME%\bin`.</span></span> <span data-ttu-id="1efdc-139">Por exemplo, usando a linha de comando:</span><span class="sxs-lookup"><span data-stu-id="1efdc-139">For instance, using command-line:</span></span>

       ```powershell
       set PATH=%HADOOP_HOME%\bin;%PATH%
       ```

<span data-ttu-id="1efdc-140">Verifique se você pode executar `dotnet`, `java`, `mvn``spark-shell` da linha de comando antes de passar para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="1efdc-140">Make sure you are able to run `dotnet`, `java`, `mvn`, `spark-shell` from your command-line before you move to the next section.</span></span> <span data-ttu-id="1efdc-141">Existe uma maneira melhor?</span><span class="sxs-lookup"><span data-stu-id="1efdc-141">Feel there is a better way?</span></span> <span data-ttu-id="1efdc-142">[Abra um problema](https://github.com/dotnet/spark/issues) e sinta-se à vontade para contribuir.</span><span class="sxs-lookup"><span data-stu-id="1efdc-142">Please [open an issue](https://github.com/dotnet/spark/issues) and feel free to contribute.</span></span>

> [!NOTE]
> <span data-ttu-id="1efdc-143">Uma nova instância da linha de comando poderá ser necessária se qualquer variável de ambiente tiver sido atualizada.</span><span class="sxs-lookup"><span data-stu-id="1efdc-143">A new instance of the command-line may be required if any environment variables were updated.</span></span>

## <a name="build"></a><span data-ttu-id="1efdc-144">{1&gt;Compilação&lt;1}</span><span class="sxs-lookup"><span data-stu-id="1efdc-144">Build</span></span>

<span data-ttu-id="1efdc-145">Para o restante deste guia, você precisará ter clonado o .NET para Apache Spark repositório em seu computador.</span><span class="sxs-lookup"><span data-stu-id="1efdc-145">For the remainder of this guide, you will need to have cloned the .NET for Apache Spark repository into your machine.</span></span> <span data-ttu-id="1efdc-146">Você pode escolher qualquer local para o repositório clonado, por exemplo, `C:\github\dotnet-spark\`.</span><span class="sxs-lookup"><span data-stu-id="1efdc-146">You can choose any location for the cloned repository, e.g., `C:\github\dotnet-spark\`.</span></span>

```bash
git clone https://github.com/dotnet/spark.git C:\github\dotnet-spark
```

### <a name="build-net-for-apache-spark-scala-extensions-layer"></a><span data-ttu-id="1efdc-147">Compilar .NET para Apache Spark camada de extensões escalares</span><span class="sxs-lookup"><span data-stu-id="1efdc-147">Build .NET for Apache Spark Scala extensions layer</span></span>

<span data-ttu-id="1efdc-148">Quando você envia um aplicativo .NET, o .NET for Apache Spark tem a lógica necessária escrita em escalares que informa Apache Spark como lidar com suas solicitações (por exemplo, solicitação para criar uma nova sessão do Spark, solicitação para transferir dados do lado do .NET para o lado da JVM, etc.).</span><span class="sxs-lookup"><span data-stu-id="1efdc-148">When you submit a .NET application, .NET for Apache Spark has the necessary logic written in Scala that informs Apache Spark how to handle your requests (e.g., request to create a new Spark Session, request to transfer data from .NET side to JVM side etc.).</span></span> <span data-ttu-id="1efdc-149">Essa lógica pode ser encontrada no [código-fonte do .net para Spark escala](https://github.com/dotnet/spark/tree/master/src/scala).</span><span class="sxs-lookup"><span data-stu-id="1efdc-149">This logic can be found in the [.NET for Spark Scala Source Code](https://github.com/dotnet/spark/tree/master/src/scala).</span></span>

<span data-ttu-id="1efdc-150">Independentemente de você estar usando o .NET Framework ou o .NET Core, será necessário criar o .NET para Apache Spark camada de extensão escalabilidade:</span><span class="sxs-lookup"><span data-stu-id="1efdc-150">Regardless of whether you are using .NET Framework or .NET Core, you will need to build the .NET for Apache Spark Scala extension layer:</span></span>

```powershell
cd src\scala
mvn clean package 
```

<span data-ttu-id="1efdc-151">Você deve ver os JARs criados para as versões do Spark com suporte:</span><span class="sxs-lookup"><span data-stu-id="1efdc-151">You should see JARs created for the supported Spark versions:</span></span>

* `microsoft-spark-2.3.x\target\microsoft-spark-2.3.x-<version>.jar`
* `microsoft-spark-2.4.x\target\microsoft-spark-2.4.x-<version>.jar`

### <a name="build-the-net-for-spark-sample-applications"></a><span data-ttu-id="1efdc-152">Compilar o .NET para aplicativos de exemplo do Spark</span><span class="sxs-lookup"><span data-stu-id="1efdc-152">Build the .NET for Spark sample applications</span></span>

<span data-ttu-id="1efdc-153">Esta seção explica como criar os [aplicativos de exemplo](https://github.com/dotnet/spark/tree/master/examples) para .net para Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="1efdc-153">This section explains how to build the [sample applications](https://github.com/dotnet/spark/tree/master/examples) for .NET for Apache Spark.</span></span> <span data-ttu-id="1efdc-154">Essas etapas ajudarão a compreender o processo de criação geral de qualquer aplicativo .NET para Spark.</span><span class="sxs-lookup"><span data-stu-id="1efdc-154">These steps will help in understanding the overall building process for any .NET for Spark application.</span></span>

#### <a name="using-visual-studio-for-net-framework"></a><span data-ttu-id="1efdc-155">Usando o Visual Studio para .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1efdc-155">Using Visual Studio for .NET Framework</span></span>

  1. <span data-ttu-id="1efdc-156">Abra `src\csharp\Microsoft.Spark.sln` no Visual Studio e compile o projeto `Microsoft.Spark.CSharp.Examples` na pasta `examples` (isso, por sua vez, criará também o projeto de associações .NET).</span><span class="sxs-lookup"><span data-stu-id="1efdc-156">Open `src\csharp\Microsoft.Spark.sln` in Visual Studio and build the `Microsoft.Spark.CSharp.Examples` project under the `examples` folder (this will in turn build the .NET bindings project as well).</span></span> <span data-ttu-id="1efdc-157">Se desejar, você pode escrever seu próprio código no projeto `Microsoft.Spark.Examples` (o ' input_file. JSON ' neste exemplo é um arquivo JSON com os dados dos quais você deseja criar o dataframe):</span><span class="sxs-lookup"><span data-stu-id="1efdc-157">If you want, you can write your own code in the `Microsoft.Spark.Examples` project (the 'input_file.json' in this example is a json file with the data you want to create the dataframe with):</span></span>
  
      ```csharp
        // Instantiate a session
        var spark = SparkSession
            .Builder()
            .AppName("Hello Spark!")
            .GetOrCreate();

        // Create initial DataFrame
        DataFrame df = spark.Read().Json(input_file.json);

        // Print schema
        df.PrintSchema();

        // Apply a filter and show results
        df.Filter(df["age"] > 21).Show();
      ```

     <span data-ttu-id="1efdc-158">Depois que a compilação for bem-sucedida, você verá os binários apropriados produzidos no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="1efdc-158">Once the build is successful, you will see the appropriate binaries produced in the output directory.</span></span>     
     <span data-ttu-id="1efdc-159">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="1efdc-159">Sample console output:</span></span>
     
      ```powershell
            Directory: C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461


        Mode                LastWriteTime         Length Name
        ----                -------------         ------ ----
        -a----         3/6/2019  12:18 AM         125440 Apache.Arrow.dll
        -a----        3/16/2019  12:00 AM          13824 Microsoft.Spark.CSharp.Examples.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.CSharp.Examples.exe.config
        -a----        3/16/2019  12:00 AM           2720 Microsoft.Spark.CSharp.Examples.pdb
        -a----        3/16/2019  12:00 AM         143360 Microsoft.Spark.dll
        -a----        3/16/2019  12:00 AM          63388 Microsoft.Spark.pdb
        -a----        3/16/2019  12:00 AM          34304 Microsoft.Spark.Worker.exe
        -a----        3/16/2019  12:00 AM          19423 Microsoft.Spark.Worker.exe.config
        -a----        3/16/2019  12:00 AM          11900 Microsoft.Spark.Worker.pdb
        -a----        3/16/2019  12:00 AM          23552 Microsoft.Spark.Worker.xml
        -a----        3/16/2019  12:00 AM         332363 Microsoft.Spark.xml
        ------------------------------------------- More framework files -------------------------------------
      ```     

#### <a name="using-net-core-cli-for-net-core"></a><span data-ttu-id="1efdc-160">Usando o CLI do .NET Core para .NET Core</span><span class="sxs-lookup"><span data-stu-id="1efdc-160">Using .NET Core CLI for .NET Core</span></span>

> [!NOTE]
> <span data-ttu-id="1efdc-161">No momento, estamos trabalhando para automatizar as compilações do .NET Core para Spark .NET.</span><span class="sxs-lookup"><span data-stu-id="1efdc-161">We are currently working on automating .NET Core builds for Spark .NET.</span></span> <span data-ttu-id="1efdc-162">Até lá, agradecemos sua paciência em executar algumas das etapas manualmente.</span><span class="sxs-lookup"><span data-stu-id="1efdc-162">Until then, we appreciate your patience in performing some of the steps manually.</span></span>

  1. <span data-ttu-id="1efdc-163">Crie o trabalho:</span><span class="sxs-lookup"><span data-stu-id="1efdc-163">Build the worker:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
      
      <span data-ttu-id="1efdc-164">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="1efdc-164">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 299.95 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 306.62 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark.Worker\Microsoft.Spark.Worker.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.Worker.dll
        Microsoft.Spark.Worker -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish\
      ```    

  2. <span data-ttu-id="1efdc-165">Compile os exemplos:</span><span class="sxs-lookup"><span data-stu-id="1efdc-165">Build the samples:</span></span>

      ```powershell
      cd C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\
      dotnet publish -f netcoreapp2.1 -r win10-x64
      ```
   
      <span data-ttu-id="1efdc-166">Exemplo de saída do console:</span><span class="sxs-lookup"><span data-stu-id="1efdc-166">Sample console output:</span></span>

      ```powershell
      PS C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples> dotnet publish -f netcoreapp2.1 -r win10-x64
      Microsoft (R) Build Engine version 16.0.462+g62fb89029d for .NET Core
      Copyright (C) Microsoft Corporation. All rights reserved.

        Restore completed in 44.22 ms for C:\github\dotnet-spark\src\csharp\Microsoft.Spark\Microsoft.Spark.csproj.
        Restore completed in 336.94 ms for C:\github\dotnet-spark\examples\Microsoft.Spark.CSharp.Examples\Microsoft.Spark.CSharp.Examples.csproj.
        Microsoft.Spark -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark\Debug\netstandard2.0\Microsoft.Spark.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\Microsoft.Spark.CSharp.Examples.dll
        Microsoft.Spark.CSharp.Examples -> C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish\
      ```     

## <a name="run-the-net-for-spark-sample-applications"></a><span data-ttu-id="1efdc-167">Executar o .NET para aplicativos de exemplo do Spark</span><span class="sxs-lookup"><span data-stu-id="1efdc-167">Run the .NET for Spark sample applications</span></span>

<span data-ttu-id="1efdc-168">Depois de criar os exemplos, executá-los será por meio de `spark-submit`, independentemente de você estar se concentrando .NET Framework ou .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1efdc-168">Once you build the samples, running them will be through `spark-submit` regardless of whether you are targeting .NET Framework or .NET Core.</span></span> <span data-ttu-id="1efdc-169">Verifique se você seguiu a seção de [pré-requisitos](#prerequisites) e instalou o Apache Spark.</span><span class="sxs-lookup"><span data-stu-id="1efdc-169">Make sure you have followed the [prerequisites](#prerequisites) section and installed Apache Spark.</span></span>

  1. <span data-ttu-id="1efdc-170">Defina a `DOTNET_WORKER_DIR` ou `PATH` variável de ambiente para incluir o caminho em que o binário `Microsoft.Spark.Worker` foi gerado (por exemplo, `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` para .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` para .NET Core):</span><span class="sxs-lookup"><span data-stu-id="1efdc-170">Set the `DOTNET_WORKER_DIR` or `PATH` environment variable to include the path where the `Microsoft.Spark.Worker` binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.Worker\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      set DOTNET_WORKER_DIR=C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.Worker\Debug\netcoreapp2.1\win10-x64\publish
      ```
  
  2. <span data-ttu-id="1efdc-171">Abra o PowerShell e vá para o diretório em que o binário do aplicativo foi gerado (por exemplo, `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` para .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` para .NET Core):</span><span class="sxs-lookup"><span data-stu-id="1efdc-171">Open Powershell and go to the directory where your app binary has been generated (e.g., `C:\github\dotnet\spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\net461` for .NET Framework, `C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish` for .NET Core):</span></span>

      ```powershell
      cd C:\github\dotnet-spark\artifacts\bin\Microsoft.Spark.CSharp.Examples\Debug\netcoreapp2.1\win10-x64\publish
      ```

  3. <span data-ttu-id="1efdc-172">A execução do aplicativo segue a estrutura básica:</span><span class="sxs-lookup"><span data-stu-id="1efdc-172">Running your app follows the basic structure:</span></span>

     ```powershell
     spark-submit.cmd `
       [--jars <any-jars-your-app-is-dependent-on>] `
       --class org.apache.spark.deploy.dotnet.DotnetRunner `
       --master local `
       <path-to-microsoft-spark-jar> `
       <path-to-your-app-exe> <argument(s)-to-your-app>
     ```

     <span data-ttu-id="1efdc-173">Aqui estão alguns exemplos que você pode executar:</span><span class="sxs-lookup"><span data-stu-id="1efdc-173">Here are some examples you can run:</span></span>

     - <span data-ttu-id="1efdc-174">**[Microsoft. Spark. examples. Sql. Batch. Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span><span class="sxs-lookup"><span data-stu-id="1efdc-174">**[Microsoft.Spark.Examples.Sql.Batch.Basic](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Batch/Basic.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Batch.Basic %SPARK_HOME%\examples\src\main\resources\people.json
         ```

     - <span data-ttu-id="1efdc-175">**[Microsoft. Spark. examples. Sql. streaming. StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="1efdc-175">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredNetworkWordCount](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredNetworkWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredNetworkWordCount localhost 9999
         ```

     - <span data-ttu-id="1efdc-176">**[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (com acesso ao Maven)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="1efdc-176">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (maven accessible)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd `
         --packages org.apache.spark:spark-sql-kafka-0-10_2.11:2.3.2 `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
         ```

     - <span data-ttu-id="1efdc-177">**[Microsoft. Spark. examples. Sql. streaming. StructuredKafkaWordCount (jars fornecidos)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span><span class="sxs-lookup"><span data-stu-id="1efdc-177">**[Microsoft.Spark.Examples.Sql.Streaming.StructuredKafkaWordCount (jars provided)](https://github.com/dotnet/spark/blob/master/examples/Microsoft.Spark.CSharp.Examples/Sql/Streaming/StructuredKafkaWordCount.cs)**</span></span>

         ```powershell
         spark-submit.cmd 
         --jars path\to\net.jpountz.lz4\lz4-1.3.0.jar,path\to\org.apache.kafka\kafka-clients-0.10.0.1.jar,path\to\org.apache.spark\spark-sql-kafka-0-10_2.11-2.3.2.jar,`path\to\org.slf4j\slf4j-api-1.7.6.jar,path\to\org.spark-project.spark\unused-1.0.0.jar,path\to\org.xerial.snappy\snappy-java-1.1.2.6.jar `
         --class org.apache.spark.deploy.dotnet.DotnetRunner `
         --master local `
         C:\github\dotnet-spark\src\scala\microsoft-spark-<version>\target\microsoft-spark-<version>.jar `
         Microsoft.Spark.CSharp.Examples.exe Sql.Streaming.StructuredKafkaWordCount localhost:9092 subscribe test
          ```
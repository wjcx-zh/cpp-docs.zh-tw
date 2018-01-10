---
title: "逐步解說： 使用 MSBuild 來建立 Visual c + + 專案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: msbuild.cpp.walkthrough.createproject
dev_langs: C++
helpviewer_keywords: 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 92b954f334517adc22ca17f8324ec1a78819d9f1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>逐步解說：使用 MSBuild 來建立 Visual C++ 專案
本逐步解說示範如何使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]建置 Visual c + + 專案，在命令提示字元。 您將學習如何建立 c + + 原始程式檔和 Visual c + + 主控台應用程式以 XML 為基礎的專案檔案。 建置專案之後, 您將學習如何自訂建置程序。  
  
 這個逐步解說將說明下列工作：  
  
-   建立 c + + 原始程式檔，為您的專案。  
  
-   建立 XML[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]專案檔。  
  
-   使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]建置專案。  
  
-   使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]來自訂您的專案。  
  
## <a name="prerequisites"></a>必要條件  
 您需要下列項目才能完成本逐步解說：  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   大致了解[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]系統。  
  
## <a name="creating-the-c-source-files"></a>建立 c + + 原始程式檔  
 在本逐步解說中，您將建立具有原始程式檔和標頭檔的專案。 來源檔案位於 main.cpp 包含主控台應用程式的 main 函式。 標頭檔 main.h 包含要包含 iostream 標頭檔的程式碼。 您可以使用來建立這些 c + + 檔案[!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]或文字編輯器。  
  
#### <a name="to-create-the-c-source-files-for-your-project"></a>若要建立專案的 c + + 原始程式檔  
  
1.  建立專案的目錄。  
  
2.  建立名為 main.cpp 的檔案，並將下列程式碼加入至這個檔案：  
  
    ```cpp  
    // main.cpp : the application source code.  
    #include <iostream>  
    #include "main.h"  
    int main()  
    {  
       std::cout << "Hello, from MSBuild!\n";  
       return 0;  
    }  
    ```  
  
3.  建立名為 main.h 的檔案，並將下列程式碼加入至這個檔案：  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## <a name="creating-the-xml-msbuild-project-file"></a>建立 XML MSBuild 專案檔案  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]專案檔是 XML 檔案，其中包含專案根項目 (\<專案 >)。 在下列範例專案中，\<專案 > 項目包含七個項目子系：  
  
-   三個項目群組標籤 (\<ItemGroup >)，指定專案組態與平台、 原始程式檔名稱，以及標頭檔名稱。  
  
-   三個匯入標記 (\<匯入 >) 旗標會指定 Microsoft Visual c + + 設定的位置。  
  
-   屬性群組標籤 (\<PropertyGroup >)，指定專案設定。  
  
#### <a name="to-create-the-msbuild-project-file"></a>若要建立 MSBuild 專案檔  
  
1.  使用文字編輯器來建立專案檔名為`myproject.vcxproj`，然後加入下列根\<專案 > 項目。 下列程序步驟之間根目錄中插入元素\<專案 > 標記：  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  加入下面兩個\<專案組態 > 中的子項目\<ItemGroup > 項目。 子項目都會指定偵錯和發行組態的 32 位元 Windows 作業系統：  
  
    ```xml  
    <ItemGroup>  
      <ProjectConfiguration Include="Debug|Win32">  
        <Configuration>Debug</Configuration>  
        <Platform>Win32</Platform>  
      </ProjectConfiguration>  
      <ProjectConfiguration Include="Release|Win32">  
        <Configuration>Release</Configuration>  
        <Platform>Win32</Platform>  
      </ProjectConfiguration>  
    </ItemGroup>  
  
    ```  
  
3.  加入下列\<匯入 / > 項目，指定這個專案的預設 c + + 設定的路徑：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  加入下列的屬性群組項目 (\<PropertyGroup >)，指定兩個專案屬性：  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  加入下列\<匯入 / > 項目，指定這個專案目前的 c + + 設定的路徑：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  加入下列\<ClCompile > 中的子項目\<ItemGroup > 項目。 子項目都會指定要編譯的 C/c + + 來源檔案的名稱：  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  加入下列\<ClInclude > 中的子項目\<ItemGroup > 項目。 子元素指定 C/c + + 原始程式檔的標頭檔的名稱：  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  加入下列\<匯入 > 項目，指定定義此專案的目標檔案的路徑：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### <a name="complete-project-file"></a>完成專案檔案  
 下列程式碼會顯示您在上一個程序中建立的完整的專案檔案。  
  
```xml  
<Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <ItemGroup>  
    <ProjectConfiguration Include="Debug|Win32">  
      <Configuration>Debug</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|Win32">  
      <Configuration>Release</Configuration>  
      <Platform>Win32</Platform>  
    </ProjectConfiguration>  
  </ItemGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  <PropertyGroup>  
    <ConfigurationType>Application</ConfigurationType>  
    <PlatformToolset>v120</PlatformToolset>  
  </PropertyGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
  <ItemGroup>  
    <ClCompile Include="main.cpp" />  
  </ItemGroup>  
  <ItemGroup>  
    <ClInclude Include="main.h" />  
  </ItemGroup>  
  <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
</Project>  
```  
  
## <a name="using-msbuild-to-build-your-project"></a>使用 MSBuild 建置您的專案  
 建置主控台應用程式的命令提示字元中輸入下列命令：  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]建立輸出檔目錄，然後編譯，並會連結您的專案以產生 Myproject.exe 程式。 建置程序完成之後，請執行應用程式中使用下列命令：  
  
```  
myproject  
```  
  
 應用程式應該會顯示"Hello，從 MSBuild ！" 。  
  
## <a name="customizing-your-project"></a>自訂您的專案  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]可讓您執行預先定義的建置目標、 套用使用者定義的屬性和使用自訂工具，事件，並建置步驟。 本章節將說明下列工作：  
  
-   使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]建置目標。  
  
-   使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]使用建置屬性。  
  
-   使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]搭配 64 位元編譯器和工具。  
  
-   使用[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]與不同的工具組。  
  
-   加入[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]自訂項目。  
  
### <a name="using-msbuild-with-build-targets"></a>使用 MSBuild 建置目標  
 A*建置目標*是一組具名的預先定義或使用者定義可以在建置期間執行的命令。 使用目標的命令列選項 (**/t**) 來指定 「 建置 」 目標。 如果是`myproject`範例專案時，預先定義**全新**目標刪除 debug 資料夾中的所有檔案，並建立新的記錄檔。  
  
 在命令提示字元中，輸入下列命令以清除`myproject`。  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### <a name="using-msbuild-with-build-properties"></a>使用 MSBuild 建置屬性  
 屬性的命令列選項 (**/p**) 可讓您覆寫您專案的組建檔案中的屬性。 在`myproject`範例專案、 版本或偵錯組建組態由指定`Configuration`屬性。 指定要執行建置的應用程式的作業系統和`Platform`屬性。  
  
 在命令提示字元中，輸入下列命令以建立偵錯版`myproject`要在 32 位元 Windows 上執行的應用程式。  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 假設`myproject`範例專案也會定義組態適用於 64 位元 Windows 和名為自訂作業系統的另一個組態`myplatform`。  
  
 在命令提示字元中，下列命令來建立發行組建的型別是 64 位元 Windows 上執行。  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 在命令提示字元中，輸入下列命令以建立的發行組建`myplatform`。  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>使用 MSBuild，搭配 64 位元編譯器和工具  
 如果您已安裝 Visual c + + 64 位元 Windows 上，依預設，會安裝 64 位元 x64 原生和跨工具。 您可以設定[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]使用 64 位元編譯器和工具來建置應用程式藉由設定`PreferredToolArchitecture`屬性。 這個屬性不會影響專案的組態或平台屬性。 根據預設，會使用 32 位元版本的工具。 若要指定 64 位元版本的編譯器和工具，將下列屬性群組項目加入至 Myproject.vcxproj 專案檔之後`Microsoft.Cpp.default.props`\<匯入 / > 項目：  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 在命令提示字元中，輸入下列命令以使用 64 位元工具來建置應用程式。  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### <a name="using-msbuild-with-a-different-toolset"></a>使用不同的工具組使用 MSBuild  
 如果您有工具組和其他版本的 Visual c + + 安裝的程式庫[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]可以建置應用程式的最新版的 Visual c + + 或其他已安裝版本。 例如，如果您已安裝[!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]，以指定 Windows xp 的 Visual c + + 11.0 工具組後面，加入下列的屬性群組項目 Myproject.vcxproj 專案檔 Microsoft.Cpp.props`<Import />`項目：  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 若要重建您的專案的 Visual c + + 11.0 的 Windows XP 工具組，請輸入下列命令：  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### <a name="adding-msbuild-customizations"></a>將加入 MSBuild 自訂項目  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]提供自訂建置流程的各種方式。 下列主題示範如何加入自訂建置步驟、 工具和事件，以您[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)]專案：  
  
-   [如何：將自訂建置步驟新增至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [如何：將自訂建置工具新增至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)
---
title: "逐步解說：使用 MSBuild 來建立 Visual C++ 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "msbuild.cpp.walkthrough.createproject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "msbuild (c++), 逐步解說：建立專案"
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 逐步解說：使用 MSBuild 來建立 Visual C++ 專案
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這個逐步解說示範如何在命令提示字元中使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 建置 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 專案。  您將學習如何為 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 主控台應用程式建立 C\+\+ 原始程式檔和 XML 專案檔。  建置專案之後，您將學習如何自訂建置流程。  
  
 這個逐步解說將說明下列工作：  
  
-   為您的專案建立 C\+\+ 原始程式檔。  
  
-   建立 XML [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 專案檔。  
  
-   使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 建置專案。  
  
-   使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 自訂專案。  
  
## 必要條件  
 您需要下列項目才能完成本逐步解說：  
  
-   [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)]  
  
-   [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 系統的一般概念了解。  
  
## 建立 C\+\+ 原始程式檔  
 在此逐步解說中，您將建立一個具有原始程式檔和標頭檔的專案。  原始程式檔 main.cpp 包含主控台應用程式的 main 函式。  標頭檔 main.h 包含用於包含 iostream 標頭檔的程式碼。  您可以使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 或文字編輯器建立這些 C\+\+ 檔。  
  
#### 若要為您的專案建立 C\+\+ 原始程式檔  
  
1.  建立專案的目錄。  
  
2.  建立名為 main.cpp 的檔案並將下列程式碼加入至這個檔案：  
  
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
  
3.  建立名為 main.h 的檔案並將下列程式碼加入至這個檔案：  
  
    ```hlsl  
    // main.h: the application header code.  
    /* Additional source code to include. */  
    ```  
  
## 建立 XML MSBuild 專案檔  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 專案檔是包含專案根項目 \(\<Project\>\) 的 XML 檔。  在下列範例專案中，\<Project\> 項目包含七個子項目：  
  
-   三個項目群組標記 \(\<ItemGroup\>\)，用於指定專案組態和平台、原始程式檔名稱和標頭檔名稱。  
  
-   三個匯入標記 \(\<Import\>\)，用於指定 Microsoft [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 設定的位置。  
  
-   屬性群組標記 \(\<PropertyGroup\>\)，用於指定專案設定。  
  
#### 若要建立 MSBuild 專案檔  
  
1.  使用文字編輯器來建立名為 `myproject.vcxproj` 的專案檔，然後加入下列根 \<Project\> 項目。  插入下列程序步驟中介於根 \<Project\> 標記之間的項目：  
  
    ```xml  
    <Project DefaultTargets="Build" ToolsVersion="12.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    </Project>  
    ```  
  
2.  在 \<ItemGroup\> 項目中加入下列兩個 \<ProjectConfiguration\> 子項目。  此子項目可指定 32 位元 Windows 作業系統的偵錯和發行組態：  
  
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
  
3.  加入下列 \<Import\/\> 項目，為此專案指定預設 C\+\+ 設定的路徑：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />  
  
    ```  
  
4.  加入下列屬性群組項目 \(\<PropertyGroup\>\)，以指定兩個專案屬性：  
  
    ```xml  
    <PropertyGroup>  
      <ConfigurationType>Application</ConfigurationType>  
      <PlatformToolset>v120</PlatformToolset>  
    </PropertyGroup>  
    ```  
  
5.  加入下列 \<Import\/\> 項目，為此專案指定目前 C\+\+ 設定的路徑：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />  
    ```  
  
6.  在 \<ItemGroup\> 項目中加入下列 \<ClCompile\> 子項目。  此子項目可指定要編譯之 C\/C\+\+ 原始程式檔的名稱：  
  
    ```xml  
    <ItemGroup>  
      <ClCompile Include="main.cpp" />  
    </ItemGroup>  
    ```  
  
7.  在 \<ItemGroup\> 項目中加入下列 \<ClInclude\> 子項目。  此子項目可指定 C\/C\+\+ 原始程式檔的標頭檔名稱：  
  
    ```xml  
    <ItemGroup>  
      <ClInclude Include="main.h" />  
    </ItemGroup>  
    ```  
  
8.  加入下列 \<Import\> 項目，為此專案指定可定義目標的檔案路徑：  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />  
  
    ```  
  
### 完成專案檔  
 下列程式碼顯示您在上一個程序中建立的完整專案檔。  
  
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
  
## 使用 MSBuild 建置專案  
 在命令提示字元中輸入下列命令，以建置主控台應用程式：  
  
```  
msbuild myproject.vcxproj /p:configuration=debug  
```  
  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 會建立輸出檔的目錄，然後編譯並連結專案，以產生 Myproject.exe 程式。  在建置流程完成之後，使用下列命令執行應用程式：  
  
```  
myproject  
```  
  
 應用程式應在主控台視窗中顯示 "Hello, from MSBuild\!"。  
  
## 自訂專案  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 可讓您執行預先定義的建置目標、套用使用者定義的屬性，以及使用自訂工具、事件和建置步驟。  這一節將說明下列工作：  
  
-   搭配使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 與建置目標。  
  
-   搭配使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 與建置屬性。  
  
-   搭配使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 與 64 位元編譯器和工具。  
  
-   搭配使用 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 與不同工具組。  
  
-   加入 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 自訂項目。  
  
### 搭配使用 MSBuild 與建置目標  
 「*建置目標*」\(Build Target\) 是預先定義或使用者定義之命令的命名集，這些命令可以在建置期間執行。  使用目標命令列選項 \(**\/t**\) 指定建置目標。  在 `myproject` 範例專案的情況中，預先定義的 **clean** 目標會刪除偵錯資料夾中的所有檔案，並建立新的記錄檔。  
  
 在命令提示字元中輸入下列命令，以清除 `myproject`。  
  
 `msbuild myproject.vcxproj /t:clean`  
  
### 搭配使用 MSBuild 與建置屬性  
 屬性命令列選項 \(**\/p**\) 可讓您覆寫專案建置檔中的屬性。  在 `myproject` 範例專案中，`Configuration` 屬性會指定發行或偵錯建置組態。  而 `Platform` 屬性會指定用於執行建置之應用程式的作業系統。  
  
 在命令提示字元中，輸入下列命令以建立要在 32 位元 Windows 上執行之 `myproject` 應用程式的偵錯組建。  
  
 `msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`  
  
 假設 `myproject` 範例專案也定義了 64 位元 Windows 的組態，並且對名稱為 `myplatform` 的自訂作業系統定義了其他組態。  
  
 在命令提示字元中，輸入下列命令以建立要在 64 位元 Windows 上執行的發行組建。  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`  
  
 在命令提示字元中，輸入下列命令以建立 `myplatform` 的發行組建。  
  
 `msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`  
  
### 搭配使用 MSBuild 與 64 位元編譯器和工具  
 如果您已在 64 位元 Windows 上安裝 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)]，根據預設會安裝 64 位元 x64 Native 和 Cross Tools。  您可以透過設定 `PreferredToolArchitecture` 屬性，設定 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 使用 64 位元編譯器和工具來建置應用程式。  這個屬性不會影響專案組態或平台屬性。  預設會使用工具的 32 位元版本。  若要指定 64 位元版編譯器及工具，請將下列屬性群組項目加入至 Myproject.vcxproj 專案檔中的 `Microsoft.Cpp.default.props` \<Import\/\> 項目之後：  
  
```xml  
<PropertyGroup>  
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>  
</PropertyGroup>  
```  
  
 在命令提示字元中輸入下列命令，以使用 64 位元工具來建置應用程式。  
  
 `msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`  
  
### 搭配使用 MSBuild 與不同 Toolset  
 如果您已安裝其他 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 版本的工具組和程式庫，[!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 可為目前的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 版本或其他已安裝版本建置應用程式。  例如，如果您已安裝 [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)]，若要指定適用於 Windows XP 的 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] 11.0 工具組，請將下列屬性群組項目加入至 Myproject.vcxproj 專案檔中的 Microsoft.Cpp.props `<Import />` 項目後面：  
  
```xml  
<PropertyGroup>  
    <PlatformToolset>v110_xp</PlatformToolset>  
</PropertyGroup>  
```  
  
 若要使用 [!INCLUDE[vcprvc](../build/includes/vcprvc_md.md)] Windows XP 11.0 工具組重新建置專案，請輸入下列任一命令：  
  
 `msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`  
  
 `msbuild myproject.vcxproj /t:rebuild`  
  
### 加入 MSBuild 自訂項目  
 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 提供各種自訂建置流程的方法。  下列主題顯示如何將自訂建置步驟、工具和事件加入至 [!INCLUDE[vstecmsbuild](../build/includes/vstecmsbuild_md.md)] 專案：  
  
-   [如何：將自訂建置步驟加入至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)  
  
-   [如何：將自訂建置工具加入至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)  
  
-   [如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)
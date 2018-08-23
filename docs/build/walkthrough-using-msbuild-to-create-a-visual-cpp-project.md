---
title: 逐步解說： 使用 MSBuild 建立 Visual c + + 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- msbuild.cpp.walkthrough.createproject
dev_langs:
- C++
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a8bb957f0ab1dd2ea7d05151257aee0e15561e8a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609695"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>逐步解說：使用 MSBuild 來建立 Visual C++ 專案

本逐步解說示範如何使用 MSBuild 來建置 Visual c + + 專案，在命令提示字元。 您將學習如何建立 c + + 原始程式檔和 Visual c + + 主控台應用程式的 XML 專案檔。 建置專案之後, 您將學習如何自訂建置流程。

這個逐步解說將說明下列工作：

- 建立您的專案的 c + + 原始程式檔。

- 建立 XML MSBuild 專案檔。

- 您可以使用 MSBuild 來建置您的專案。

- 您可以使用 MSBuild，自訂您的專案。

## <a name="prerequisites"></a>必要條件

您需要下列項目才能完成本逐步解說：

- Visual Studio 中使用一份**使用 c + + 的桌面開發**安裝工作負載。

- MSBuild 系統大致的了解。

> [!NOTE]
> 如果您想要使用 Visual Studio IDE 在稍後編輯專案檔，請勿使用此方法。 如果您以手動方式建立.vcxproj 檔案，Visual Studio IDE 可能無法編輯或載入它，特別是當專案在專案項目中使用萬用字元。

> [!NOTE]
> 中包含大部分的低層級的組建指示 **.targets**並 **.props** VCTargets 目錄，儲存在屬性中所定義的檔案`$(VCTargetsPath)`。 Visual Studio 2017 Enterprise Edition 中的這些檔案的預設路徑為 c:\\Program Files (x86)\\Microsoft Visual Studio\\2017年\\Enterprise\\Common7\\IDE\\VC\\VCTargets\\。

## <a name="creating-the-c-source-files"></a>建立 c + + 原始程式檔

在本逐步解說中，您將建立具有原始程式檔和標頭檔的專案。 原始程式檔 main.cpp 包含主控台應用程式的 main 函式。 標頭檔 main.h 包含要包含 iostream 標頭檔的程式碼。 您可以使用 Visual Studio 或文字建立這些 c + + 檔案，如 Visual Studio Code 的編輯器。

### <a name="to-create-the-c-source-files-for-your-project"></a>若要建立您的專案的 c + + 原始程式檔

1. 建立您的專案目錄。

2. 建立名為 main.cpp 的檔案，並將下列程式碼新增至此檔案：

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

3. 建立名為 main.h 的檔案，並將下列程式碼新增至此檔案：

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>建立 XML MSBuild 專案檔

MSBuild 專案檔是 XML 檔案，其中包含專案根項目 (\<專案 >)。 在下列範例專案中，\<專案 > 項目包含七個子項目：

- 三個項目群組標記 (\<ItemGroup >)，以指定專案組態與平台、 原始程式檔名稱及標頭檔名稱。

- 三個匯入標記 (\<匯入 >)，指定 Microsoft Visual c + + 設定的位置。

- 屬性群組標記 (\<PropertyGroup >)，指定專案設定。

### <a name="to-create-the-msbuild-project-file"></a>若要建立 MSBuild 專案檔

1. 使用文字編輯器來建立專案檔案，稱為`myproject.vcxproj`，然後加入下列根\<專案 > 項目。 在下列程序步驟中的根之間插入元素\<專案 > 標記：

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

2. 新增下列兩個\<ProjectConfiguration > 中的子項目\<ItemGroup > 項目。 子項目指定偵錯和發行適用於 32 位元 Windows 作業系統的組態：

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

3. 新增下列\<匯入 / > 項目，指定這個專案的預設 c + + 設定的路徑：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

4. 新增下列屬性群組項目 (\<PropertyGroup >)，指定兩個專案屬性：

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v141</PlatformToolset>
    </PropertyGroup>
    ```

5. 新增下列\<匯入 / > 項目，指定目前 c + + 設定此專案的路徑：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

6. 新增下列\<ClCompile > 中的子項目\<ItemGroup > 項目。 子元素會指定要編譯的 C/c + + 來源檔案的名稱：

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > \<ClCompile > 已*建置目標*且定義在**VCTargets**目錄。

7. 新增下列\<ClInclude > 中的子項目\<ItemGroup > 項目。 子元素會指定 C/c + + 原始程式檔的標頭檔的名稱：

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

8. 新增下列\<匯入 > 項目，指定定義此專案的目標檔案的路徑：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>完成的專案檔

下列程式碼會顯示您在上一個程序中建立完整的專案檔。

```xml
<Project DefaultTargets="Build" ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
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
    <PlatformToolset>v141</PlatformToolset>
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

## <a name="using-msbuild-to-build-your-project"></a>使用 MSBuild 來建置您的專案

建置主控台應用程式的命令提示字元中輸入下列命令：

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild 會建立輸出檔目錄，然後編譯並連結專案，以產生 Myproject.exe 程式。 建置程序完成之後，請執行應用程式中使用下列命令：

`myproject`

應用程式應該會顯示"Hello，from MSBuild ！" 。

## <a name="customizing-your-project"></a>自訂您的專案

MSBuild 可讓您執行預先定義的建置目標、 套用使用者定義的屬性，並使用自訂工具、 事件與建置步驟。 本章節將說明下列工作：

- 您可以使用 MSBuild 與建置目標。

- 使用 MSBuild 與建置屬性。

- 您可以使用 MSBuild 與 64 位元編譯器和工具。

- 使用 MSBuild 與不同的工具組。

- 加入 MSBuild 自訂項目。

### <a name="using-msbuild-with-build-targets"></a>使用 MSBuild 與建置目標

A*建置目標*是一組具名的預先定義或使用者定義可以在建置期間執行的命令。 使用目標命令列選項 (**/t**) 來指定組建的目標。 若是`myproject`範例專案中，預先定義**全新**目標會刪除偵錯資料夾中的所有檔案，並建立新的記錄檔。

在命令提示字元中，輸入下列命令，以清除`myproject`。

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>使用 MSBuild 與建置屬性

屬性的命令列選項 (**/p**) 可讓您覆寫專案建置檔中的屬性。 在 `myproject`範例專案、 發行或偵錯組建組態由`Configuration`屬性。 指定要執行建置的應用程式的作業系統和`Platform`屬性。

在命令提示字元中，輸入下列命令以建立偵錯組建`myproject`要在 32 位元 Windows 上執行的應用程式。

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

假設`myproject`範例專案也會定義組態，64 位元 Windows 和適用於名為自訂作業系統的另一個組態`myplatform`。

在命令提示字元中，輸入下列命令來建立發行組建，是在 64 位元 Windows 上執行。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

在命令提示字元中，輸入下列命令來建立的發行組建`myplatform`。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>使用 MSBuild 與 64 位元編譯器和工具

如果您已安裝在 64 位元 Windows 上的 Visual c + +，根據預設，會安裝 64 位元 x64 native 和 cross tools。 您可以設定 MSBuild 來建置您的應用程式設定中使用的 64 位元編譯器和工具`PreferredToolArchitecture`屬性。 這個屬性不會影響專案組態或平台屬性。 根據預設，會使用 32 位元版本的工具。 若要指定 64 位元版本的編譯器和工具，將下列屬性群組項目加入至 Myproject.vcxproj 專案檔之後`Microsoft.Cpp.default.props`\<匯入 / > 項目：

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

在命令提示字元中，輸入下列命令，以使用 64 位元工具來建置您的應用程式。

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>使用 MSBuild 與不同 toolset

如果您有針對其他版本的安裝的 Visual c + + 程式庫與工具組，MSBuild 就可以建置應用程式的目前 Visual c + + 版本或其他已安裝的版本。 比方說，如果您已安裝 Visual Studio 2012，指定 Visual c + + 11.0 工具組適用於 Windows XP 中，新增下列屬性群組項目至 Myproject.vcxproj 專案檔之後 Microsoft.Cpp.props`<Import />`項目：

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

若要重建您的 Visual c + + 11.0 的 Windows XP 工具組的專案，輸入下列命令：

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

`msbuild myproject.vcxproj /t:rebuild`

### <a name="adding-msbuild-customizations"></a>加入 MSBuild 自訂項目

MSBuild 會提供各種自訂建置流程。 下列主題顯示如何將自訂建置步驟、 工具和事件新增至您的 MSBuild 專案：

- [如何：將自訂建置步驟新增至 MSBuild 專案](../build/how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [如何：將自訂建置工具新增至 MSBuild 專案](../build/how-to-add-custom-build-tools-to-msbuild-projects.md)

- [如何：在 MSBuild 專案中使用建置事件](../build/how-to-use-build-events-in-msbuild-projects.md)

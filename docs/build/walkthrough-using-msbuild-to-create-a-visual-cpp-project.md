---
title: 逐步解說：使用 MSBuild 建立 Visual C++ 專案
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), walkthrough: create a project'
ms.assetid: 52350d1c-c373-4868-923c-5e8be6f67adb
ms.openlocfilehash: c93867f3be3b17f703c549aa5c05f3d327934c26
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837597"
---
# <a name="walkthrough-using-msbuild-to-create-a-visual-c-project"></a>逐步解說：使用 MSBuild 建立 Visual C++ 專案

本逐步解說將示範如何使用 MSBuild 在命令提示字元上建置 Visual Studio C++ 專案。 您將了解如何為 Visual C++ 主控台應用程式建立 C++ 來源檔案和 XML 架構的專案檔。 建置專案之後，您將了解如何自訂建置流程。

這個逐步解說將說明下列工作：

- 為您的專案建立 C++ 來源檔案。

- 建立 XML MSBuild 專案檔。

- 使用 MSBuild 建置專案。

- 使用 MSBuild 自訂專案。

## <a name="prerequisites"></a>必要條件

您需要下列項目才能完成本逐步解說：

- 一份 Visual Studio 複本，其中已安裝**使用 C++ 的桌面開發**工作負載。

- 對 MSBuild 系統有大致的了解。

> [!NOTE]
> 如果您稍後要使用 Visual Studio IDE 來編輯專案檔，請勿使用此方法。 如果您以手動方式建立 .vcxproj 檔案，Visual Studio IDE 可能無法編輯或載入該檔案，特別是專案在專案項目中使用萬用字元時。

> [!NOTE]
> 大部分的低層級組建指示都會包含在 VCTargets 目錄中定義的 **.targets** 和 **.props** 檔案中，並儲存在 `$(VCTargetsPath)` 屬性中。 在 Visual Studio 2019 Enterprise 版本中，這些檔案的預設路徑為 C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\MSBuild\Microsoft\VC\v160\Microsoft.Cpp.Common.props。

## <a name="creating-the-c-source-files"></a>建立 C++ 來源檔案

在本逐步解說中，您將建立具有來源檔案和標頭檔的專案。 來源檔案 main.cpp 包含用於主控台應用程式的 main 函式。 標頭檔 main.h 包含要包含 iostream 標頭檔的程式碼。 您可以使用 Visual Studio 或 Visual Studio Code 之類的文字編輯器來建立這些 C++ 檔案。

### <a name="to-create-the-c-source-files-for-your-project"></a>為您的專案建立 C++ 來源檔案

1. 建立專案的目錄。

1. 建立名為 main.cpp 的檔案，並將下列程式碼新增至此檔案：

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

1. 建立名為 main.h 的檔案，並將下列程式碼新增至此檔案：

    ```cpp
    // main.h: the application header code.
    /* Additional source code to include. */
    ```

## <a name="creating-the-xml-msbuild-project-file"></a>建立 XML MSBuild 專案檔

MSBuild 專案檔是包含專案根項目 (`<Project>`) 的 XML 檔案。 在下列範例專案中，`<Project>` 項目包含七個子項目：

- 三個項目群組標記 (`<ItemGroup>`)，用來指定專案組態與平台、來源檔案名稱及標頭檔名稱。

- 三個匯入標記 (`<Import>`)，用來指定 Microsoft Visual C++ 設定的位置。

- 屬性群組標記 (`<PropertyGroup>`)，用來指定專案設定。

### <a name="to-create-the-msbuild-project-file"></a>建立 MSBuild 專案檔

1. 使用文字編輯器來建立名為 `myproject.vcxproj` 的專案檔，然後加入下列根 `<Project>` 項目。 在下列程序步驟的根 `<Project>` 標記之間插入元素。 (如果您使用 Visual Studio 2017，請使用 ToolsVersion ="15.0"，如果您使用 Visual Studio 2019，請使用 ToolsVersion="16.0"。)

    ```xml
    <Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    </Project>
    ```

1. 在 `<ItemGroup>` 項目中新增下列兩個 `<ProjectConfiguration>` 子項目。 子項目會指定適用於 32 位元 Windows 作業系統的偵錯和版本設定：

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

1. 新增下列 `<Import>` 項目，以指定此專案的預設 C++ 設定路徑：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.default.props" />
    ```

1. 新增下列屬性群組項目 (`<PropertyGroup>`)，以指定兩個專案屬性。 (如果您使用 Visual Studio 2017，請使用 v141，如果您使用 Visual Studio 2019，請使用 v142)。

    ```xml
    <PropertyGroup>
      <ConfigurationType>Application</ConfigurationType>
      <PlatformToolset>v142</PlatformToolset>
    </PropertyGroup>
    ```

1. 新增下列 `<Import>` 項目，以指定此專案的目前 C++ 設定路徑：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.props" />
    ```

1. 在 `<ItemGroup>` 項目中新增下列 `<ClCompile>` 子項目。 子項目會為要編譯的 C/C++ 來源檔案指定名稱：

    ```xml
    <ItemGroup>
      <ClCompile Include="main.cpp" />
    </ItemGroup>
    ```

   > [!NOTE]
   > `<ClCompile>` 是「建置目標」，且定義於 **VCTargets** 目錄中。

1. 在 `<ItemGroup>` 項目中新增下列 `<ClInclude>` 子項目。 子項目會為 C/C++ 來源檔案的標頭檔指定名稱：

    ```xml
    <ItemGroup>
      <ClInclude Include="main.h" />
    </ItemGroup>
    ```

1. 新增下列 `<Import>` 項目，為定義此專案目標的檔案指定路徑：

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.Targets" />
    ```

### <a name="complete-project-file"></a>完成專案檔

下列程式碼會顯示上一個程序中建立的完整專案檔。 (若使用 Visual Studio 2017，請使用 ToolsVersion ="15.0"。)

```xml
<Project DefaultTargets="Build" ToolsVersion="16.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
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
    <PlatformToolset>v142</PlatformToolset>
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

## <a name="using-msbuild-to-build-your-project"></a>使用 MSBuild 建置專案

在命令提示字元中輸入下列命令，以建置主控台應用程式：

`msbuild myproject.vcxproj /p:configuration=debug`

MSBuild 會建立輸出檔案的目錄，然後編譯並連結專案，以產生 Myproject.exe 程式。 建置程序完成之後，請使用下列命令從 [偵錯] 資料夾中執行應用程式：

`myproject`

應用程式應該會顯示 "Hello, from MSBuild!" 。

## <a name="customizing-your-project"></a>自訂專案

MSBuild 可讓您執行預先定義的建置目標、套用使用者定義的屬性，以及使用自訂工具、事件與建置步驟。 本節將說明下列工作：

- 搭配使用 MSBuild 與建置目標。

- 搭配使用 MSBuild 與建置屬性。

- 搭配使用 MSBuild 與 64 位元編譯器和工具。

- 搭配使用 MSBuild 與不同工具組。

- 新增 MSBuild 自訂項目。

### <a name="using-msbuild-with-build-targets"></a>搭配使用 MSBuild 與建置目標

「建置目標」是一組具名的預先定義或使用者定義命令，可以在建置期間執行。 使用目標命令列選項 (`/t`) 來指定建置目標。 針對 `myproject` 範例專案，預先定義的 **clean** 目標會刪除偵錯資料夾中的所有檔案，並且建立新的記錄檔。

在命令提示字元中輸入下列命令，即可清除 `myproject`。

`msbuild myproject.vcxproj /t:clean`

### <a name="using-msbuild-with-build-properties"></a>搭配使用 MSBuild 與建置屬性

屬性命令列選項 (`/p`) 可讓您覆寫專案建置檔案中的屬性。 在 `myproject` 範例專案中，`Configuration` 屬性會指定版本或偵錯建置組態。 而 `Platform` 屬性會指定要執行建置應用程式的作業系統。

在命令提示字元中，輸入下列命令以建立 `myproject` 應用程式的偵錯建置，此應用程式會在 32 位元的 Windows 上執行。

`msbuild myproject.vcxproj /p:configuration=debug /p:platform=win32`

我們假設 `myproject` 範例專案也會定義適用於 64 位元 Windows 的組態，以及另一個適用於 `myplatform` 自訂作業系統的組態。

在命令提示字元中，輸入下列命令來建立可在 64 位元 Windows 上執行的發行組建。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=x64`

在命令提示字元中，輸入下列命令來建立 `myplatform` 的發行組建。

`msbuild myproject.vcxproj /p:configuration=release /p:platform=myplatform`

### <a name="using-msbuild-with-the-64-bit-compiler-and-tools"></a>搭配使用 MSBuild 與 64 位元編譯器和工具

如果您已在 64 位元 Windows 上安裝 Visual Studio，根據預設，64 位元的 x64 原生和交叉工具也會一併安裝。 您可以藉由設定 `PreferredToolArchitecture` 屬性，將 MSBuild 設定為使用 64 位元編譯器和工具來建置應用程式。 此屬性不會影響專案組態或平台屬性。 根據預設，系統會使用 32 位元版本的工具。 若要指定 64 位元版本的編譯器和工具，請將下列屬性群組項目加到 Myproject.vcxproj 專案檔的 `Microsoft.Cpp.default.props` \<Import /> 項目後面：

```xml
<PropertyGroup>
    <PreferredToolArchitecture>x64</PreferredToolArchitecture>
</PropertyGroup>
```

在命令提示字元中輸入下列命令，即可使用 64 位元工具來建置應用程式。

`msbuild myproject.vcxproj /p:PreferredToolArchitecture=x64`

### <a name="using-msbuild-with-a-different-toolset"></a>搭配使用 MSBuild 與不同工具組

如果您有安裝適用於其他 Visual C++ 版本的工具組與程式庫，MSBuild 可以針對目前的 Visual C++ 版本或其他已安裝的版本來建置應用程式。 例如，如果您已安裝 Visual Studio 2012，若要指定適用於 Windows XP 的 Visual C++ 11.0 工具組，請將下列屬性群組項目加入 Myproject.vcxproj 專案檔的 `Microsoft.Cpp.props` \<Import /> 項目後面：

```xml
<PropertyGroup>
    <PlatformToolset>v110_xp</PlatformToolset>
</PropertyGroup>
```

若要以 Visual C++ 11.0 Windows XP 工具組重建您的專案，請輸入下列命令：

`msbuild myproject.vcxproj /p:PlatformToolset=v110_xp /t:rebuild`

### <a name="adding-msbuild-customizations"></a>新增 MSBuild 自訂項目

MSBuild 會提供各種自訂建置流程的方式。 下列主題會示範如何將自訂建置步驟、工具和事件新增至您的 MSBuild 專案：

- [如何：將自訂建置步驟新增至 MSBuild 專案](how-to-add-a-custom-build-step-to-msbuild-projects.md)

- [如何：將自訂建置工具新增至 MSBuild 專案](how-to-add-custom-build-tools-to-msbuild-projects.md)

- [如何：在 MSBuild 專案中使用建置事件](how-to-use-build-events-in-msbuild-projects.md)

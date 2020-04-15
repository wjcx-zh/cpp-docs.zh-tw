---
title: 進階屬性頁(專案)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 8ce62b768f5cda30501e791bcd040a40b18bfb23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81328417"
---
# <a name="advanced-property-page"></a>進階屬性頁

高級屬性頁面在 Visual Studio 2019 及更高版本提供。

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>進階屬性

- **目的地檔案副檔名**

   指定要用於生成輸出的檔副檔名。 預設為 **.exe**的應用程式,靜態庫的 **.lib**和 DLL 的 **.dll。**

- **清除時要刪除的副檔名**

   [清除]**** 選項 ([建置]**** 功能表) 會從建置專案組態的中繼目錄刪除檔案。 具有此屬性所指定副檔名的檔案，將會在執行 [清除]**** 時或您執行重建時刪除。 除了中繼目錄裡這些副檔名的檔案，建置系統也會刪除任何已知的建置輸出，而不論其所在位置 (包括像是 .obj 檔的中繼輸出)。 請注意，您可以指定萬用字元。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

- **建置記錄檔**

   可讓您指定每當建置專案時建立記錄檔的非預設位置。 預設位置是由巨集 $(IntDir)$(MSBuildProjectName).log 所指定。

   若要變更目錄位置，您可以使用專案巨集。 有關[產生指令和屬性,請參閱通用巨集](common-macros-for-build-commands-and-properties.md)。

- **預設建構工具架構結構**

   指定是使用 x86 還是 x64 產生工具。

- **使用除錯庫**

   指定是創建 DEBUG 還是"釋放"

- **開啟統一 (JUMBO) 產生**

   啟用生成過程,其中許多C++源檔在編譯前合併到一個或多個"統一"檔中,以提高生成性能。 與 Unity 遊戲引擎無關。

- **MFC 用途**

   指定 MFC 專案將會靜態還是動態連結至 MFC DLL。 非 MFC 專案可選取 [使用標準的視窗程式庫]**** 連結至使用 MFC 時包含的各種 Win32 程式庫。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

- **字元集**

   定義是否應該設定 _UNICODE 或 _MBCS。 在適當的地方，也會影響連結器進入點。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

- **整個程式最佳化**

   指定 [/GL](gl-whole-program-optimization.md) 編譯器選項和 [/LTCG](ltcg-link-time-code-generation.md) 連結器選項。 根據預設，偵錯組態會停用此選項，而零售組態會啟用此選項。

- **MSVC 工具集版本**

   指定將用於生成專案的 MSVC 工具集的完整版本。 如果安裝了工具集的各種更新和預覽版本,則可以在此處指定要使用的版本。

## <a name="ccli-properties"></a>C++/CLI 屬性

- **Common Language Runtime 支援**

   導致使用 [/clr](clr-common-language-runtime-compilation.md) 編譯器選項。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

- **目標 .NET Framework 版本**

   在受控專案中，指定目標 .NET Framework 版本。

- **啟用受控累加建置**

   對於受控專案，這會在您產生組件時啟用外部可見度的偵測。 如果其他專案看不到受控專案的變更，則不會重建相依專案。 如此可大幅改善方案 (包括受控專案) 的建置時間。

::: moniker-end

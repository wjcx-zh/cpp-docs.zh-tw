---
title: Advanced 屬性頁 (專案)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315527"
---
# <a name="advanced-property-page"></a>Advanced 屬性頁

[Advanced] 屬性頁在 Visual Studio 2019 和更新版本中提供。

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>進階屬性

- **目標副檔名**

   指定要用於組建輸出的副檔名。 預設為適用于應用程式的 **.exe** 、用於靜態程式庫的 **.lib**和 dll 的 **.dll** 。

- **清除時要刪除的副檔名**

   [清除]  選項 ([建置]  功能表) 會從建置專案組態的中繼目錄刪除檔案。 具有此屬性所指定副檔名的檔案，將會在執行 [清除]  時或您執行重建時刪除。 除了中繼目錄裡這些副檔名的檔案，建置系統也會刪除任何已知的建置輸出，而不論其所在位置 (包括像是 .obj 檔的中繼輸出)。 請注意，您可以指定萬用字元。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

- **建置記錄檔**

   可讓您指定每當建置專案時建立記錄檔的非預設位置。 預設位置是由巨集 $(IntDir)$(MSBuildProjectName).log 所指定。

   若要變更目錄位置，您可以使用專案巨集。 請參閱[組建命令和屬性的一般宏](common-macros-for-build-commands-and-properties.md)。

- **慣用的組建工具架構**

   指定是否要使用 x86 或 x64 build 工具。

- **使用 Debug 程式庫**

   指定是否要建立 DEBUG 或 RELEASE 組建。

- **啟用 Unity (巨型) 組建**

   啟用在編譯之前將許多C++原始程式檔結合成一或多個 "unity" 檔案的組建程式, 以改善組建效能。 與 Unity 遊戲引擎無關。

- **MFC 用途**

   指定 MFC 專案將會靜態還是動態連結至 MFC DLL。 非 MFC 專案可選取 [使用標準的視窗程式庫]  連結至使用 MFC 時包含的各種 Win32 程式庫。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

- **字元集**

   定義是否應該設定 _UNICODE 或 _MBCS。 在適當的地方，也會影響連結器進入點。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

- **整個程式最佳化**

   指定 [/GL](gl-whole-program-optimization.md) 編譯器選項和 [/LTCG](ltcg-link-time-code-generation.md) 連結器選項。 根據預設，偵錯組態會停用此選項，而零售組態會啟用此選項。

- **MSVC 工具組版本**

   指定將用來建立專案的完整版本 MSVC 工具組。 如果您已安裝各種更新和預覽版本的工具組, 您可以在這裡指定要使用哪一個。

## <a name="ccli-properties"></a>C++/CLI 屬性

- **Common Language Runtime 支援**

   導致使用 [/clr](clr-common-language-runtime-compilation.md) 編譯器選項。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

- **目標 .NET Framework 版本**

   在受控專案中，指定目標 .NET Framework 版本。

- **啟用受控累加建置**

   對於受控專案，這會在您產生組件時啟用外部可見度的偵測。 如果其他專案看不到受控專案的變更，則不會重建相依專案。 如此可大幅改善方案 (包括受控專案) 的建置時間。

::: moniker-end

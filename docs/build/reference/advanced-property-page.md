---
title: " (專案) 的 Advanced 屬性頁"
ms.date: 08/10/2020
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: 3d6694e44d3da4023998a0335cd06c85b353b2b1
ms.sourcegitcommit: 8140647370017b885432349ce89f187c3068b46a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144161"
---
# <a name="advanced-property-page"></a>Advanced 屬性頁

::: moniker range="<=vs-2017"

[Advanced] 屬性頁在 Visual Studio 2019 和更新版本中提供。 若要查看該版本的檔，請將本文的 Visual Studio**版本**選取器控制項設定為 Visual Studio 2019。 您可在此頁面的目錄頂端找到該檔案。

::: moniker-end

::: moniker range="vs-2019"

[Advanced] 屬性頁在 Visual Studio 2019 和更新版本中提供。

## <a name="advanced-properties"></a>進階屬性

- **目標副檔名**

   指定要用於組建輸出的副檔名。 適用于 *`.exe`* 應用程式的、 *`.lib`* 靜態程式庫和 dll 的預設值 *`.dll`* 。

- **清除時要刪除的副檔名**

   [清除]**** 選項 ([建置]**** 功能表) 會從建置專案組態的中繼目錄刪除檔案。 當執行**Clean**或重建時，會刪除此屬性中指定之副檔名的檔案。 組建系統會刪除中繼目錄中具有這些副檔名的任何檔案。 它也會刪除任何已知的組建輸出，不論其位於何處。 包含中繼輸出的 (，例如 *`.obj`* files。 ) 您可以在這個屬性中指定萬用字元。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>。

- **建置記錄檔**

   可讓您針對每次建立專案時所建立的記錄檔，指定非預設的位置。 預設位置是由宏指定 `$(IntDir)$(MSBuildProjectName).log` 。

   若要變更目錄位置，您可以使用專案巨集。 請參閱[組建命令和屬性的一般宏](common-macros-for-build-commands-and-properties.md)。

- **慣用的組建工具架構**

   指定是否要使用 x86 或 x64 build 工具。

- **使用 Debug 程式庫**

   指定是否要建立 Debug 或 Release 組建。

- **啟用 Unity (巨型) 組建**

   啟用更快速的組建程式，將許多 c + + 來源檔案結合成一個或多個檔案，然後再進行編譯。 這些合併的檔案稱為*unity*檔案。 它們與 Unity 遊戲引擎無關。

- **將內容複寫到 OutDir**

   將專案中標示為*內容*的專案複製到專案的輸出目錄， (`$(OutDir)`) 。 此設定可簡化部署。 從 Visual Studio 2019 16.7 版開始提供此屬性。

- **將專案參考複製到 OutDir**

   將可執行檔 (DLL 和 EXE 檔案) 專案參考專案複製到專案的輸出目錄 (`$(OutDir)`) 。 在 c + +/CLI ([`/clr`](clr-common-language-runtime-compilation.md)) 專案中，會忽略這個屬性。 相反地，每個專案參考上的 [**複製到本機**] 屬性會控制是否複製到輸出目錄。 此設定可簡化本機部署。 從 Visual Studio 2019 16.7 版開始提供。

- **將專案參考的符號複製到 OutDir**

   將專案參考專案的 PDB 檔案連同專案參考可執行檔專案複製到專案的輸出目錄， (`$(OutDir)`) 。 C + +/CLI 專案一律會啟用此屬性。 此設定可簡化 debug 部署。 從 Visual Studio 2019 16.7 版開始提供。

- **將 c + + 執行時間複製到 OutDir**

   將執行時間 Dll 複製到專案的輸出目錄， (`$(OutDir)`) 。 此設定可簡化本機部署。 從 Visual Studio 2019 16.7 版開始提供。

- **MFC 用途**

   指定 MFC 專案是以靜態或動態方式連結至 MFC DLL。 在非 MFC 專案中，選取 [**使用標準 Windows 程式庫**] 連結 MFC 所包含的 Win32 程式庫。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>。

- **字元集**

   定義是否 `_UNICODE` `_MBCS` 應該設定或。 在適當的地方，也會影響連結器進入點。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>。

- **整個程式最佳化**

   指定 [`/GL`](gl-whole-program-optimization.md) 編譯器選項和 [`/LTCG`](ltcg-link-time-code-generation.md) 連結器選項。 根據預設，會停用整個程式優化以進行 Debug 設定，並啟用發行設定。

- **MSVC 工具組版本**

   指定用來建立專案的完整版本 MSVC 工具組。 您可能已安裝各種更新和預覽版本的工具組。 您可以在這裡指定要使用哪一個。

## <a name="ccli-properties"></a>C + +/CLI 屬性

- **Common Language Runtime 支援**

   會 [`/clr`](clr-common-language-runtime-compilation.md) 使用編譯器選項。

   若要以程式設計方式存取此屬性，請參閱 <xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>。

- **目標 .NET Framework 版本**

   在受控專案中，指定目標 .NET Framework 版本。

- **啟用受控累加建置**

   若為 managed 專案，此選項可在您產生元件時偵測外部可見度。 如果其他專案看不到 managed 專案的變更，則不會重建相依專案。 受管理的累加組建可以大幅改善包含受控專案之方案中的組建時間。

::: moniker-end

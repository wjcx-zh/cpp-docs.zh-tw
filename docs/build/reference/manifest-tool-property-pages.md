---
title: 資訊清單工具屬性頁
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: d9b074667614da8d83fae7b00b49bf63c9390b69
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927683"
---
# <a name="manifest-tool-property-pages"></a>資訊清單工具屬性頁

使用這些頁面來指定[mt.exe](/windows/win32/sbscs/mt-exe)的一般選項。 這些頁面會在 [**專案** > **屬性** > 設定] [**屬性** > ] [**資訊清單工具**] 下找到。

## <a name="general-property-page"></a>一般屬性頁

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

   [是 (/ nologo)] 指定資訊清單工具啟動時，要隱藏標準 Microsoft 著作權資料。 當您執行 mt.exe 作為建置程序的一部分，或從建置環境執行時，使用此選項來隱藏記錄檔中不想要的輸出。

### <a name="verbose-output"></a>詳細資訊輸出

   [是 (/verbose)] 指定在資訊清單產生過程將會顯示其他組建資訊。

### <a name="assembly-identity"></a>元件識別 * *

使用 /identity 選項指定識別字串，其中包含 [\<assemblyIdentity> 項目](/visualstudio/deployment/assemblyidentity-element-clickonce-application)的屬性。 識別字串開頭為 `name` 屬性的值，後面接著 *attribute* = *value* 組。 識別字串中的屬性是以逗號分隔。

這是範例身分識別字串：`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>輸入和輸出屬性頁     

###  <a name="additional-manifest-files"></a>其他資訊清單檔案

使用 **/manifest** 選項來指定資訊清單工具將處理或合併之其他資訊清單檔的完整路徑。 完整路徑以分號分隔。 （-資訊清單 [manifest1] [manifest2] ...）

###  <a name="input-resource-manifests"></a>輸入資源資訊清單

使用 **/inputresource** 選項來指定型別為 RT_MANIFEST 的資源完整路徑，以輸入至資訊清單工具。 路徑後面可以接著指定的資源識別碼。 例如：

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>內嵌資訊清單

- [是] 指定專案系統會將應用程式資訊清單檔內嵌至組件。

- [否] 指定專案系統會將應用程式資訊清單檔建立為獨立檔案。

###  <a name="output-manifest-file"></a>輸出資訊清單檔

指定輸出資訊清單檔的名稱。 當資訊清單工具只有操作一個資訊清單檔案時，這個屬性為選擇性。 （-out： [file]; # [資源識別碼]）

###  <a name="manifest-resource-file"></a>資訊清單資源檔

指定用來將資訊清單嵌入專案輸出的輸出資源檔。

###  <a name="generate-catalog-files"></a>產生類別目錄檔案

使用 **/makecdfs** 選項指定資訊清單工具會產生用來製作目錄的類別目錄定義檔 (.cdf 檔)。 /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>從 ManagedAssembly 產生資訊清單

從受控組件產生資訊清單。 （-managedassemblyname： [file]）

###  <a name="suppress-dependency-element"></a>隱藏 Dependency 元素

與-managedassembly 搭配使用。 抑制最後資訊清單中的相依性元素產生。 (-nodependency)

###  <a name="generate-category-tags"></a>產生類別標記

與-managedassembly 搭配使用。 -category 會產生類別標記。 （-category）

###  <a name="dpi-awareness"></a>DPI 感知

指定是否為 DPI 感知應用程式。 根據預設，對於 MFC 專案此設定為 [是]，其他則為 [否]，因為只有 MFC 專案有內建的 DPI 感知。 如果您新增程式碼來處理不同 DPI 設定，可以將設定覆寫為 [是]。 如果您將非 DPI 感知的應用程式設定為 DPI 感知，您的應用程式可能顯得模糊或變小。

**做**

- **無**
- **高 DPI 感知**
- **每個監視器高 DPI 感知**

## <a name="isolated-com-property-page"></a>隔離的 COM 屬性頁

如需有關隔離的 COM 的詳細資訊，請 參閱[隔離的應用程式](/windows/win32/SbsCs/isolated-applications)和如[何：建立隔離的應用程式以使用](../how-to-build-isolated-applications-to-consume-com-components.md)COM 元件。

###  <a name="type-library-file"></a>類型程式庫檔案

指定要用於 regfree COM 資訊清單支援的類型程式庫。 （-tlb： [檔案]）

###  <a name="registrar-script-file"></a>註冊機構腳本檔案

指定要用於 regfree COM 資訊清單支援的註冊機構腳本檔案。 （-rgs： [檔案]）

###  <a name="component-file-name"></a>元件檔名稱

指定從指定的 .tlb 或 .rgs 所建立之元件的檔案名。 （-dll： [檔案]）

###  <a name="replacements-file"></a>取代檔案

指定包含 RGS 檔案中可取代字串值的檔案。 （取代專案： [檔案]）

## <a name="advanced-property-page"></a>Advanced 屬性頁

###  <a name="update-file-hashes"></a>更新檔案雜湊

計算檔案專案中指定之檔案的雜湊，並以這個值更新雜湊屬性。 （hashupdate： [路徑]）

###  <a name="update-file-hashes-search-path"></a>更新檔案雜湊搜尋路徑

指定更新檔案雜湊時要使用的搜尋路徑。

###  <a name="additional-options"></a>其他選項

其他選項


## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)

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
ms.openlocfilehash: e1d0f1ac889cb915216ceb70d48e36efe4ad21bc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336302"
---
# <a name="manifest-tool-property-pages"></a>資訊清單工具屬性頁

使用這些頁面為[Mt.exe](/windows/win32/sbscs/mt-exe)指定常規選項。 這些頁面位於**專案** > **屬性** > **配置屬性** > **清單工具**下。

## <a name="general-property-page"></a>一般屬性頁

### <a name="suppress-startup-banner"></a>隱藏啟動橫幅

   [是 (/ nologo)]**** 指定資訊清單工具啟動時，要隱藏標準 Microsoft 著作權資料。 當您執行 mt.exe 作為建置程序的一部分，或從建置環境執行時，使用此選項來隱藏記錄檔中不想要的輸出。

### <a name="verbose-output"></a>詳細輸出

   [是 (/verbose)]**** 指定在資訊清單產生過程將會顯示其他組建資訊。

### <a name="assembly-identity"></a>組件識別

使用 /識別選項指定標識字串,該字串包含[\<程式集標識>元素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)的屬性。 `name`標識字串以 屬性的值開頭,後跟*屬性* = *值*對。 識別字串中的屬性是以逗號分隔。

這是範例識別字串:`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>輸入與輸出屬性頁

### <a name="additional-manifest-files"></a>其他資訊清單檔

使用 **/manifest** 選項來指定資訊清單工具將處理或合併之其他資訊清單檔的完整路徑。 完整路徑以分號分隔。 (-清單[清單1][清單2]...)

### <a name="input-resource-manifests"></a>輸入資源資訊清單

使用 **/inputresource** 選項來指定型別為 RT_MANIFEST 的資源完整路徑，以輸入至資訊清單工具。 路徑後面可以接著指定的資源識別碼。 例如：

`dll_with_manifest.dll;#1`

### <a name="embed-manifest"></a>內嵌資訊清單

- [是]**** 指定專案系統會將應用程式資訊清單檔內嵌至組件。

- [否]**** 指定專案系統會將應用程式資訊清單檔建立為獨立檔案。

### <a name="output-manifest-file"></a>輸出資訊清單檔

指定輸出資訊清單檔的名稱。 當資訊清單工具只有操作一個資訊清單檔案時，這個屬性為選擇性。 (外:[檔];[資源 ID])

### <a name="manifest-resource-file"></a>資訊清單資源檔

指定用來將資訊清單嵌入專案輸出的輸出資源檔。

### <a name="generate-catalog-files"></a>產生目錄檔

使用 **/makecdfs** 選項指定資訊清單工具會產生用來製作目錄的類別目錄定義檔 (.cdf 檔)。 (/makecdfs)

### <a name="generate-manifest-from-managedassembly"></a>從 ManagedAssembly 產生資訊清單

從受控組件產生資訊清單。 (託管程式集名稱:\[檔案)

### <a name="suppress-dependency-element"></a>隱藏相依性項目

與 -託管裝配一起使用。 禁止生成最終清單中的依賴項元素。 (-不依賴)

### <a name="generate-category-tags"></a>產生分類標記

與 -託管裝配一起使用。 -類別導致生成類別標記。 (類別)

### <a name="dpi-awareness"></a>DPI 意識

指定是否為 DPI 感知應用程式。 根據預設，對於 MFC 專案此設定為 [是]****，其他則為 [否]****，因為只有 MFC 專案有內建的 DPI 感知。 如果您新增程式碼來處理不同 DPI 設定，可以將設定覆寫為 [是]****。 如果您將非 DPI 感知的應用程式設定為 DPI 感知，您的應用程式可能顯得模糊或變小。

**Choices**

- **None**
- **高 DPI 感知**
- **每個監視器高 DPI 感知**

## <a name="isolated-com-property-page"></a>隔離 COM 屬性頁

有關隔離 COM 的詳細資訊,請參考[隔離應用程式](/windows/win32/SbsCs/isolated-applications)以及如何[:建立獨立應用程式以使用 COM 元件](../how-to-build-isolated-applications-to-consume-com-components.md)。

### <a name="type-library-file"></a>型別程式庫檔案

指定用於註冊免費 COM 清單支援的類型庫。 (-tlb:[檔案])

### <a name="registrar-script-file"></a>登錄器指令碼檔

指定用於註冊商腳本檔以用於註冊 COM 清單支援。 (-rgs:[檔案])

### <a name="component-file-name"></a>元件檔名稱

指定從指定的 .tlb 或 .rgs 產生的元件的檔名。 (-dll:[檔案])

### <a name="replacements-file"></a>取代檔案

指定包含 RGS 檔中可取代字串的值的檔案。 (替換:[檔案])

## <a name="advanced-property-page"></a>進階屬性頁

### <a name="update-file-hashes"></a>更新檔案雜湊

計算檔元素中指定的檔的哈希值,並更新具有此值的哈希屬性。 (哈希更新:[路徑])

### <a name="update-file-hashes-search-path"></a>更新檔案雜湊搜尋路徑

指定更新檔案哈希時要使用的搜索路徑。

### <a name="additional-options"></a>其他選項

其他選項

## <a name="see-also"></a>另請參閱

[C++專案屬性頁參考](property-pages-visual-cpp.md)

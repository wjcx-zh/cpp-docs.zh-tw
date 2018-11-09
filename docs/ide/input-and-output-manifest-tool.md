---
title: 資訊清單工具輸入與輸出屬性 (Visual C++)
ms.date: 08/27/2018
f1_keywords:
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.DependencyInformationFile
- VC.Project.VCManifestTool.OutputResourceManifest
- VC.Project.VCManifestTool.GenerateCatalogFiles
ms.assetid: a8bb20f6-7ace-45ca-bab0-b4f4a5caf170
ms.openlocfilehash: 8aa007e41cdabe0bf548f1184b801c1f81655596
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624691"
---
# <a name="input-and-output-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>輸入和輸出、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊

使用此對話方塊即可指定 [Mt.exe](/windows/desktop/SbsCs/mt-exe) 的輸入與輸出選項。

若要存取此屬性頁對話方塊，請開啟您專案或屬性工作表的屬性頁。 展開 [組態屬性] 下的 [資訊清單工具] 節點，然後選取 [輸入和輸出]。

## <a name="uielement-list"></a>UIElement 清單

**其他資訊清單檔**<br/>
使用 **/manifest** 選項來指定資訊清單工具將處理或合併之其他資訊清單檔的完整路徑。 完整路徑以分號分隔。

**輸入資源資訊清單**<br/>
使用 **/inputresource** 選項來指定型別為 RT_MANIFEST 的資源完整路徑，以輸入至資訊清單工具。 路徑後面可以接著指定的資源識別碼。 例如: 

`dll_with_manifest.dll;#1`

資源識別碼是選擇性的，預設值為 CREATEPROCESS_MANIFEST_RESOURCE_ID winuser.h。

**內嵌資訊清單**<br/>
- [是] 指定專案系統會將應用程式資訊清單檔內嵌至組件。

- [否] 指定專案系統會將應用程式資訊清單檔建立為獨立檔案。

**輸出資訊清單檔**<br/>
指定輸出資訊清單檔的名稱。 當資訊清單工具只有操作一個資訊清單檔案時，這個屬性為選擇性。

**資訊清單資源檔**<br/>
指定用來將資訊清單嵌入專案輸出的輸出資源檔。

**產生目錄檔**<br/>
使用 **/makecdfs** 選項指定資訊清單工具會產生用來製作目錄的類別目錄定義檔 (.cdf 檔)。

**從 ManagedAssembly 產生資訊清單**<br/>
從受控組件產生資訊清單。 (**-managedassemblyname:**<em>file</em>)。

**隱藏相依性項目**<br/>
搭配 **-managedassembly** 選項使用。 這個標記會在最後資訊清單中隱藏相依性項目的建立。

**產生分類標記**<br/>
搭配 **-managedassembly** 選項使用。 這個標記會導致產生分類標記。

**啟用 DPI 感知**<br/>
指定是否為 DPI 感知應用程式。 根據預設，對於 MFC 專案此設定為 [是]，其他則為 [否]，因為只有 MFC 專案有內建的 DPI 感知。 如果您新增程式碼來處理不同 DPI 設定，可以將設定覆寫為 [是]。 如果您將非 DPI 感知的應用程式設定為 DPI 感知，您的應用程式可能顯得模糊或變小。

## <a name="see-also"></a>請參閱

[ndptecclick](/visualstudio/deployment/clickonce-application-manifest)<br/>
[資訊清單工具屬性頁](../ide/manifest-tool-property-pages.md)<br/>
[使用專案屬性](../ide/working-with-project-properties.md)<br/>

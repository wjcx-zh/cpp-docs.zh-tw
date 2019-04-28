---
title: 資訊清單工具屬性隔離的 COM
ms.date: 12/10/2018
f1_keywords:
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.ReplacementsFile
ms.assetid: 457582b8-cfde-49c0-92e3-3a6b9e8c08eb
ms.openlocfilehash: 2fda169ecf304373d27d699bf313bde124dc399f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269709"
---
# <a name="isolated-com-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>隔離的 COM、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊

使用此對話方塊即可指定 [Mt.exe](https://msdn.microsoft.com/library/aa375649) 的 [隔離的 COM] 選項。

若要存取此屬性頁對話方塊，請開啟您專案或屬性工作表的屬性頁。 展開 [通用屬性] 下的 [資訊清單工具] 節點，然後選取 [隔離的 COM]。

## <a name="task-list"></a>工作清單

- [如何：建置隔離的應用程式以取用 COM 元件](../how-to-build-isolated-applications-to-consume-com-components.md)

## <a name="uielement-list"></a>UIElement 清單

- **型別程式庫檔案**

   使用 /tlb 選項來指定資訊清單工具將用來產生資訊清單檔案的型別程式庫檔案 (.tlb 檔) 名稱。

- **登錄器指令碼檔**

   使用 /rgs 選項來指定資訊清單工具將用來產生資訊清單檔案的登錄器指令碼檔案 (.rgs 檔) 名稱。

- **元件檔名稱**

   使用 /dll 選項來指定資訊清單工具將產生之資源的名稱。 當指定 [型別程式庫檔案] 或 [登錄器指令碼檔] 的值時，您必須輸入此屬性的值。

- **取代檔案**

   使用 /replacements 選項指定包含 .rgs 檔中可取代字串值的檔案完整路徑。

## <a name="see-also"></a>另請參閱

[隔離的應用程式](/windows/desktop/SbsCs/isolated-applications)<br>
[ndptecclick](/visualstudio/deployment/clickonce-application-manifest)<br>
[資訊清單工具屬性頁](manifest-tool-property-pages.md)<br>
[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)

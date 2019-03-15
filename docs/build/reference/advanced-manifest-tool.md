---
title: 進階、 資訊清單工具、 組態屬性、&lt;專案名稱 > 屬性頁對話方塊
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCManifestTool.KeyFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- VC.Project.VCManifestTool.ValidateSignature
- VC.Project.VCManifestTool.KeyContainer
ms.assetid: 3d587366-05ea-4956-a978-313069660735
ms.openlocfilehash: a20e474deb69099c53ad656dda5406e7161a1695
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57824972"
---
# <a name="advanced-manifest-tool-configuration-properties-ltprojectnamegt-property-pages-dialog-box"></a>進階、資訊清單工具、組態屬性、&lt;Projectname&gt; 屬性頁對話方塊

使用此對話方塊即可指定 [Mt.exe](https://msdn.microsoft.com/library/aa375649) 的進階選項。

若要存取此屬性頁對話方塊，請開啟您專案或屬性工作表的屬性頁。 展開 [組態屬性] 下的 [資訊清單工具] 節點，然後選取 [進階]。

## <a name="uielement-list"></a>UIElement 清單

- **更新檔案雜湊**

   使用 /hashupdate 選項來指定資訊清單工具將會計算 `<file>` 項目中指定的檔案雜湊，然後以計算值更新雜湊屬性。

- **更新檔案雜湊搜尋路徑**

   指定 `<file>` 項目中所參考檔案的搜尋路徑。 此選項也會使用 /hashupdate 選項。

## <a name="see-also"></a>另請參閱

[\<file> 元素](/visualstudio/deployment/file-element-clickonce-application)<br>
[ndptecclick](/visualstudio/deployment/clickonce-application-manifest)<br>
[資訊清單工具屬性頁](manifest-tool-property-pages.md)<br>
[設定 c + + 編譯器和建置在 Visual Studio 中的屬性](../working-with-project-properties.md)

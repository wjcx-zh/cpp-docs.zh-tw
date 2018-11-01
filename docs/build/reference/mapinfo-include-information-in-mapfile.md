---
title: /MAPINFO (將資訊包括在對應檔中)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.MapLines
- VC.Project.VCLinkerTool.MapInfoFixups
- VC.Project.VCLinkerTool.MapExports
- /mapinfo
helpviewer_keywords:
- /MAPINFO linker option
- MAPINFO linker option
- -MAPINFO linker option
ms.assetid: 533d2bce-f9b7-4fea-ae1c-0b4864c9d10b
ms.openlocfilehash: bfb8273a8299349ea9aa0b78f1ee14a6cbb6276c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440309"
---
# <a name="mapinfo-include-information-in-mapfile"></a>/MAPINFO (將資訊包括在對應檔中)

```
/MAPINFO:EXPORTS
```

## <a name="remarks"></a>備註

/MAPINFO 選項會告訴連結器在對應檔，如果您指定建立包含指定的資訊[/typedefs/ 對應](../../build/reference/map-generate-mapfile.md)選項。  EXPORTS 會告訴連結器包含匯出的函式。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**對應匯出**屬性：

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapExports%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
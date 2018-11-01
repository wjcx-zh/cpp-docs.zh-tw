---
title: /MAP (產生對應檔)
ms.date: 11/04/2016
f1_keywords:
- /map
- VC.Project.VCLinkerTool.MapFileName
- VC.Project.VCLinkerTool.GenerateMapFile
helpviewer_keywords:
- mapfiles, creating linker
- generate mapfile linker option
- mapfile linker option
- mapfiles, information about program being linked
- MAP linker option
- -MAP linker option
- mapfiles, specifying file name
- /MAP linker option
ms.assetid: 9ccce53d-4e36-43da-87b0-7603ddfdea63
ms.openlocfilehash: 8ff2a8f54caa54247050c607004ed328c0d1b11d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436450"
---
# <a name="map-generate-mapfile"></a>/MAP (產生對應檔)

```
/MAP[:filename]
```

## <a name="arguments"></a>引數

*filename*<br/>
使用者指定對應檔名稱。 它會取代預設的名稱。

## <a name="remarks"></a>備註

/MAP 選項會告訴連結器建立對應檔。

根據預設，連結器會命名對應檔的程式和延伸模組.map 基底名稱。 選擇性*filename*可讓您覆寫對應檔的預設名稱。

對應檔是文字檔，其中包含所要連結程式的下列資訊：

- 模組名稱，這就是檔案的基底名稱

- 程式檔案標頭 （不是從檔案系統） 的時間戳記

- 在程式中，與每個群組的起始位址的群組清單 (以*一節*:*位移*)，長度、 群組名稱和類別

- 公用符號，每個位址的清單 (以*一節*:*位移*)，符號名稱、 一般位址，以及已定義符號的.obj 檔案

- 進入點 (作為*一節*:*位移*)

[/MAPINFO](../../build/reference/mapinfo-include-information-in-mapfile.md)選項會指定要包含在對應檔中的其他資訊。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **偵錯**屬性頁。

1. 修改**產生對應檔**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateMapFile%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.MapFileName%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
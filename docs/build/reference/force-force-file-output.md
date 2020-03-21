---
title: /FORCE (強制檔案輸出)
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: d1d85174290faa95e73c63a25f7d80c554e83ace
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079621"
---
# <a name="force-force-file-output"></a>/FORCE (強制檔案輸出)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>備註

/FORCE 選項會指示連結器建立有效的 .exe 檔或 DLL，即使符號已被參考但未定義或已進行乘法定義也一樣。

/FORCE 選項可以接受選擇性引數：

- 使用/FORCE： MULTIPLE 來建立輸出檔，不論連結是否會尋找一個以上的符號定義。

- 使用/FORCE：無法解析來建立輸出檔，不論連結是否找到未定義的符號。 /FORCE：如果無法解析進入點符號，則會忽略無法解析的。

不含引數的/FORCE 會隱含多個和無法解析。

使用此選項建立的檔案可能無法如預期般執行。 當指定/FORCE 選項時，連結器不會以累加方式連結。

如果模組是使用 **/clr**編譯， **/force**將不會建立映射。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 以滑鼠右鍵按一下**方案總管**中的專案，然後選擇 [**屬性**]。

1. 按一下 **Linker** 資料夾。

1. 按一下 [命令列] 屬性頁。

1. 在 [**其他選項**] 方塊中輸入選項。

如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱＜<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>＞。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)

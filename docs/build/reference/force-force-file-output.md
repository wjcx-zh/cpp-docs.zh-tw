---
title: /FORCE (強制檔案輸出)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
ms.openlocfilehash: af7962a4b3b5805e7e0c4d59752254c8ade17f7b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814302"
---
# <a name="force-force-file-output"></a>/FORCE (強制檔案輸出)

```
/FORCE:[MULTIPLE|UNRESOLVED]
```

## <a name="remarks"></a>備註

/FORCE 選項會指示連結器，以建立有效的.exe 檔或 DLL 即使符號參考但未定義或多次定義。

/FORCE 選項可以採取的選擇性引數：

- 使用 /force: multiple 都會建立輸出檔，不論是否連結找到一個以上的符號定義。

- 使用 /FORCE： 無法解析的建立輸出檔案，不論是否連結找到未定義的符號。 / 強制： 無法解析未解析進入點符號是否會被忽略。

/ 強制不含引數隱含多次，而無法解析。

使用這個選項建立的檔案可能無法如預期執行。 指定 /FORCE 選項時，不會將以累加方式連結，連結器。

如果模組以編譯 **/clr**， **/force**將不會建立映像。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入到選項**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)

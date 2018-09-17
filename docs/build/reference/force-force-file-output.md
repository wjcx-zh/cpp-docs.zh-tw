---
title: -FORCE （強制檔案輸出） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.ForceLink
- /force
dev_langs:
- C++
helpviewer_keywords:
- FORCE linker option
- file output in linker
- /FORCE linker option
- -FORCE linker option
ms.assetid: b1e9a218-a5eb-4e60-a4a4-65b4be15e5da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a746a37183f26585fd013327a964b922589221
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45699761"
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

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 [命令列]  屬性頁。

1. 輸入到選項**其他選項** 方塊中。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
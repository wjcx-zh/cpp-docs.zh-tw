---
title: -HEAP （設定堆積大小） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- /heap
- VC.Project.VCLinkerTool.HeapReserveSize
dev_langs:
- C++
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2f853b46c9a4cc2ec8f396be2b2f8355270ccf95
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702690"
---
# <a name="heap-set-heap-size"></a>/HEAP (設定堆積大小)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>備註

/HEAP 選項會設定堆積的大小，以位元組為單位。 建置的.exe 檔案時，此選項會是僅供使用。

*保留*引數會指定虛擬記憶體中堆積配置總和。 預設的堆積大小為 1 MB。 連結器會無條件進位到最接近的 4 個位元組指定的值。

選擇性`commit`引數會指定一次配置的實體記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 較高`commit`值可以節省的時間，當應用程式需要較多的堆積空間，但會增加記憶體需求和可能的啟動時間。

指定*保留*和`commit`十進位或 C 語言標記法中的值。

這項功能也會提供模組定義檔與透過[HEAPSIZE](../../build/reference/heapsize.md)。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 設定 Visual c + + 專案屬性](../../ide/working-with-project-properties.md)。

1. 按一下 **連結器**資料夾。

1. 按一下 **系統**屬性頁。

1. 修改**堆積基本配置大小**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。

## <a name="see-also"></a>另請參閱

[設定連結器選項](../../build/reference/setting-linker-options.md)<br/>
[連結器選項](../../build/reference/linker-options.md)
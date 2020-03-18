---
title: /HEAP (設定堆積大小)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.HeapCommitSize
- VC.Project.VCLinkerTool.HeapReserveSize
helpviewer_keywords:
- -HEAP linker option
- heap allocation, setting heap size
- /HEAP linker option
- HEAP linker option
ms.assetid: a3f71927-7f1d-492c-9fdb-dfccb1a043da
ms.openlocfilehash: f155ad56ec1a90479b402e38e7ec7f3e3d80e470
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439519"
---
# <a name="heap-set-heap-size"></a>/HEAP (設定堆積大小)

```
/HEAP:reserve[,commit]
```

## <a name="remarks"></a>備註

/HEAP 選項會設定堆積的大小（以位元組為單位）。 只有在建立 .exe 檔案時，才使用此選項。

*Reserve*引數會指定虛擬記憶體中的堆積配置總數。 預設堆積大小為 1 MB。 連結器會將指定的值舍入至最接近的4個位元組。

選擇性的 `commit` 引數會指定一次配置的實體記憶體數量。 已認可的虛擬記憶體會導致在分頁檔中保留空間。 當應用程式需要更多堆積空間時，較高的 `commit` 值可節省時間，但會增加記憶體需求和啟動時間。

以 decimal 或 C 語言標記法指定*保留*和 `commit` 值。

您也可以透過具有[HEAPSIZE](heapsize.md)的模組定義檔取得這種功能。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 按一下 **Linker** 資料夾。

1. 按一下 [**系統**] 屬性頁。

1. 修改 [**堆積認可大小**] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

- 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapReserveSize%2A> 和 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.HeapCommitSize%2A>。

## <a name="see-also"></a>另請參閱

[MSVC 連結器參考](linking.md)<br/>
[MSVC 連結器選項](linker-options.md)

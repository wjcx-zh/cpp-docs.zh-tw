---
title: /HEAP
ms.date: 11/04/2016
f1_keywords:
- /heap
helpviewer_keywords:
- heap allocation, setting heap size
- HEAP editbin option
- -HEAP editbin option
- /HEAP editbin option
ms.assetid: 6ce759b5-75b7-44ff-a5fd-3a83a0ba9a48
ms.openlocfilehash: 24470c00afce54bab0a15dd08e03cef6dfee63fc
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415249"
---
# <a name="heap"></a>/HEAP

設定堆積的大小 (位元組)。 這個選項只適用於可執行檔。

```

/HEAP:
reserve[,commit]
```

## <a name="remarks"></a>備註


  `reserve` 引數會指定虛擬記憶體中初始堆積配置的總計。 預設的堆積大小為 1 MB。 [EDITBIN 參考](../../build/reference/editbin-reference.md)會無條件進位到最接近的 4 個位元組指定的值。

選擇性`commit`引數受限於由作業系統的解譯方式。 在 Windows 作業系統上，它指定要配置的實體記憶體數量，以及必須展開堆積時要配置的額外記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 當應用程式需要較多的堆積空間時，較高的 `commit` 值允許系統的記憶體配置較不頻繁，但會增加記憶體需求且可能增加啟動時間。 
  `commit` 值必須小於或等於 `reserve` 值。

以十進位數或以 C 語言十六進位或八進位標記法指定 `reserve` 值和 `commit` 值。 例如，1 MB 的值以十進位表示為 1048576，以十六位元表示為 0x100000，以八進位表示為 04000000。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)

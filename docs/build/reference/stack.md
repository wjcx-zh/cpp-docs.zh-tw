---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack_editbin
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 63fcddec8ff8afd81084bb5a2786f394db594b07
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438892"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>備註

此選項會設定堆疊的大小（以位元組為單位），並採用十進位或 C 語言標記法中的引數。 /STACK 選項只適用于可執行檔。

*Reserve*引數會指定虛擬記憶體中的總堆疊配置。 EDITBIN 會將指定的值四捨五入到最接近的4個位元組。

選擇性的 `commit` 引數會受到作業系統的轉譯。 在 Windows NT、Windows 95 和 Windows 98 中，`commit` 指定一次配置的實體記憶體數量。 已認可的虛擬記憶體會導致在分頁檔中保留空間。 較高的 `commit` 值可節省應用程式需要更多堆疊空間的時間，但會增加記憶體需求和可能的啟動時間。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](editbin-options.md)

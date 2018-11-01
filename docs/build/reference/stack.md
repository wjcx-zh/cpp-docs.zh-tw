---
title: /STACK
ms.date: 11/04/2016
f1_keywords:
- /stack
helpviewer_keywords:
- -STACK editbin option
- STACK editbin option
- stack, setting size
- /STACK editbin option
ms.assetid: a39bcff0-c945-4355-80cc-8e4f24a5f142
ms.openlocfilehash: 89591a9d0a7f19422275b6bce6f4c5a7a723e800
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50647699"
---
# <a name="stack"></a>/STACK

```
/STACK:reserve[,commit]
```

## <a name="remarks"></a>備註

這個選項會設定堆疊大小 （位元組），並採用引數，以十進位或 C 語言表示法。 /STACK 選項僅適用於可執行檔。

*保留*引數會指定虛擬記憶體中堆疊配置總量。 EDITBIN 會無條件進位到最接近的 4 個位元組指定的值。

選擇性`commit`引數受限於由作業系統的解譯方式。 在 Windows NT、 Windows 95 和 Windows 98`commit`指定一次配置的實體記憶體數量。 已認可的虛擬記憶體會造成要保留在分頁檔的空間。 較高`commit`值可以節省的時間，當應用程式需要較多的堆疊空間，但會增加記憶體需求且可能啟動時間。

## <a name="see-also"></a>另請參閱

[EDITBIN 選項](../../build/reference/editbin-options.md)
---
title: 語彙基元評估
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152543"
---
# <a name="evaluation-of-tokens"></a>語彙基元評估

當編譯器解譯語彙基元時，會盡可能將更多字元納入單一語彙基元中，再進行至下一個語彙基元。 因此，如果語彙基元未以空白字元正確分隔，編譯器就可能因為上述行為而無法依照您預期的方式解譯語彙基元。 以下列運算式為例：

```
i+++j
```

在這個範例中，編譯器會先從三個加號盡可能產生最長的運算子 (`++`)，然後將其餘加號當做加法運算子處理 (`+`)。 因此，運算式會解譯為 `(i++) + (j)`，而不是 `(i) + (++j)`。 在這類情況下，使用空白字元和括號可避免模稜兩可的情形，並確保正確求出運算式的值。

**Microsoft 專屬**

C 編譯器會將 CTRL+Z 字元視為檔案結尾指標。 它會忽略 CTRL+Z 之後的任何文字。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[C 語彙基元](../c-language/c-tokens.md)

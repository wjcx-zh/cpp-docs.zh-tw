---
title: 連結器工具警告 LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 0b18002135d225a90f7e45adc2ff57a64c0a79f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50531014"
---
# <a name="linker-tools-warning-lnk4092"></a>連結器工具警告 LNK4092

共用的可寫入區段 'section' 含有重新配置;映像可能無法正確執行

連結器會發出這個警告，只要有一個共用的小節來警告您潛在嚴重的問題。

多個處理序之間共用資料的一個方式是一個區段標示為 「 共用 」。 不過，標示為共用的區段可能會造成問題。 例如，您有包含宣告的方式共用的 data 區段中的 DLL:

```
int var = 1;
int *pvar = &var;
```

連結器無法解析`pvar`因為 DLL 載入記憶體中的位置取決於它的值，因此它重新配置將記錄放置在 DLL 中。 當 DLL 載入記憶體的位址`var`可以解決和`pvar`指派。 如果另一個處理序載入相同的 DLL，但卻無法載入在相同位址，重新配置的位址`var`第二個程序和第一個處理序位址空間，將指向錯誤的位址將會更新。
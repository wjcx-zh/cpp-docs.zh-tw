---
title: 運算錯誤 M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: 986c0e53edcddfc47eb9ba970f3c32385e0a57d9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225185"
---
# <a name="math-error-m6111"></a>運算錯誤 M6111

堆疊下溢

浮點運算導致8087/287/387 副處理器或模擬器上的堆疊下溢。

此錯誤通常是因為呼叫不會傳回值的函式所造成 **`long double`** 。 例如，下列程式會在編譯和執行時產生此錯誤：

```
long double ld() {};
main ()
{
  ld();
}
```

程式終止，結束代碼為139。

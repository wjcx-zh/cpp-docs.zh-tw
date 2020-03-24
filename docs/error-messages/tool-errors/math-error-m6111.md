---
title: 運算錯誤 M6111
ms.date: 11/04/2016
f1_keywords:
- M6111
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
ms.openlocfilehash: e8abedf6a326a826d0c8ac513b15037c8bf89bce
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80173687"
---
# <a name="math-error-m6111"></a>運算錯誤 M6111

堆疊下溢

浮點運算導致8087/287/387 副處理器或模擬器上的堆疊下溢。

此錯誤通常是因為呼叫不會傳回值的 `long double` 函數所造成。 例如，下列程式會在編譯和執行時產生此錯誤：

```
long double ld() {};
main ()
{
  ld();
}
```

程式終止，結束代碼為139。

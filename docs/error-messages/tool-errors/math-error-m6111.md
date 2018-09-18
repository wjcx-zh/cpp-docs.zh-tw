---
title: 運算錯誤 M6111 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 95a55ec6b7cdf0b6e4c15bd283dde77c610698fa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46074821"
---
# <a name="math-error-m6111"></a>運算錯誤 M6111

stack 反向溢位

浮點運算導致 8087/287/387 副處理器或模擬器上的堆疊反向溢位。

此錯誤通常因為呼叫`long double`不傳回值的函式。 例如，下列會產生此錯誤時編譯並執行：

```
long double ld() {};
main ()
{
  ld();
}
```

程式結束，結束代碼 139。
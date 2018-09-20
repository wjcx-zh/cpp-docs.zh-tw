---
title: __noop |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __noop_cpp
- __noop
dev_langs:
- C++
helpviewer_keywords:
- __noop keyword [C++]
ms.assetid: 81ac6e97-7bf8-496b-b3c4-fd02837573e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97820367f0960925dfcac1db339260cd3f52b8bc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430211"
---
# <a name="noop"></a>__noop

**Microsoft 專屬**

`__noop`內建函式會指定應該忽略函式和剖析引數清單，但沒有程式碼產生的引數。 它適用於接受可變數目的引數的全域偵錯函式中。

編譯器會將轉換`__noop`0 在編譯時期內建函式。

## <a name="example"></a>範例

下列程式碼示範如何使用`__noop`。

```
// compiler_intrinsics__noop.cpp
// compile with or without /DDEBUG
#include <stdio.h>

#if DEBUG
   #define PRINT   printf_s
#else
   #define PRINT   __noop
#endif

int main() {
   PRINT("\nhello\n");
}
```

## <a name="see-also"></a>另請參閱

[編譯器內建](../intrinsics/compiler-intrinsics.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)
---
title: 編譯器警告（層級1） C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 92cb9a063a2f6e4660c3f84516527c1417c55e46
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966142"
---
# <a name="compiler-warning-level-1-c4393"></a>編譯器警告（層級1） C4393

' var '： const 對常值資料成員沒有影響;忽略

[常](../../extensions/literal-cpp-component-extensions.md)值資料成員也指定為 const。  由於常值資料成員意指 const，因此您不需要將 const 加入至宣告。

下列範例會產生 C4393：

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
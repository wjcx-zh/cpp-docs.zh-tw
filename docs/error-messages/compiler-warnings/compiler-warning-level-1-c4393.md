---
title: 編譯器警告 (層級 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: edc09bd48614abe3ea06d4365cb55110f8b9956b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162708"
---
# <a name="compiler-warning-level-1-c4393"></a>編譯器警告 (層級 1) C4393

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

---
title: 編譯器警告 (層級 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 4226c8ecd41e890d70fa5741decae605d45b620f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386924"
---
# <a name="compiler-warning-level-1-c4393"></a>編譯器警告 (層級 1) C4393

'var': const 對常值資料成員; 沒有任何作用已忽略

A[常值](../../extensions/literal-cpp-component-extensions.md)也指定為 const 資料成員。  常值資料成員隱含 const，因為您不需要將 const 加入宣告。

下列範例會產生 C4393:

```
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
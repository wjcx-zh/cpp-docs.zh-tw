---
title: 編譯器錯誤 C3241
ms.date: 11/04/2016
f1_keywords:
- C3241
helpviewer_keywords:
- C3241
ms.assetid: 2ca14879-bba0-4a23-b22a-72cfff92d6a4
ms.openlocfilehash: 6a618a9c538558d2aa4b995cbc9071bb8e94a5bc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754572"
---
# <a name="compiler-error-c3241"></a>編譯器錯誤 C3241

' method '：這個方法不是由 ' interface ' 引進

當您明確覆寫函式時，函數簽章必須完全符合您要覆寫之函式的宣告。

下列範例會產生 C3241：

```cpp
// C3241.cpp
#pragma warning(disable:4199)

__interface IX12A {
   void mf();
};

__interface IX12B {
   void mf(int);
};

class CX12 : public IX12A, public IX12B { // C3241
   void IX12A::mf(int);
};
```

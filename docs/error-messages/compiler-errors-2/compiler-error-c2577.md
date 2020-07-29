---
title: 編譯器錯誤 C2577
ms.date: 11/04/2016
f1_keywords:
- C2577
helpviewer_keywords:
- C2577
ms.assetid: fc79ef83-8362-40a2-9257-8037c3195ce4
ms.openlocfilehash: 0a7c711fa399c1bf31bc9de61f0b77ad19172a73
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206909"
---
# <a name="compiler-error-c2577"></a>編譯器錯誤 C2577

' member '：析構函式/完成項不能有傳回類型

「析構函式」或「完成項」無法傳回的值 **`void`** 或任何其他類型。 請 **`return`** 從析構函式定義中移除語句。

## <a name="example"></a>範例

下列範例會產生 C2577。

```cpp
// C2577.cpp
// compile with: /c
class A {
public:
   A() {}
   ~A(){
      return 0;   // C2577
   }
};
```

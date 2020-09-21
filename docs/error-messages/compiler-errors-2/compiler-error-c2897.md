---
title: 編譯器錯誤 C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: 22e63ce92a6d526f08e68bedb35de104be339dc3
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743369"
---
# <a name="compiler-error-c2897"></a>編譯器錯誤 C2897

函式/完成項不可以是函式範本

無法多載析構函式或完成項，因此將「析構函數」宣告為範本 (這會定義一組不允許的一組析構函式) 。

## <a name="examples"></a>範例

下列範例會產生 C2897。

```cpp
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

下列範例會產生 C2897。

```cpp
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```

---
title: 編譯器錯誤 C2897
ms.date: 11/04/2016
f1_keywords:
- C2897
helpviewer_keywords:
- C2897
ms.assetid: a88349e2-823f-42a0-8660-0653b677afa4
ms.openlocfilehash: 264ad52a10c6cf19d1105561f1140cf2d3e2f8e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378839"
---
# <a name="compiler-error-c2897"></a>編譯器錯誤 C2897

解構函式/完成項不可為函式樣板

解構函式或完成項無法多載，因此不允許宣告解構函式做為範本 （這會定義一組的解構函式）。

下列範例會產生 C2897:

## <a name="example"></a>範例

下列範例會產生 C2897。

```
// C2897.cpp
// compile with: /c
class X {
public:
   template<typename T> ~X() {}   // C2897
};
```

## <a name="example"></a>範例

下列範例會產生 C2897。

```
// C2897_b.cpp
// compile with: /c /clr
ref struct R2 {
protected:
   template<typename T> !R2(){}   // C2897 error
};
```
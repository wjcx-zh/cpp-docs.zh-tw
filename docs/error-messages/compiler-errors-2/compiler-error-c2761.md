---
title: 編譯器錯誤 C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: fbe2b3089d387d356073febf2b27bbb44b6be7e3
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759499"
---
# <a name="compiler-error-c2761"></a>編譯器錯誤 C2761

' function '：不允許成員函式重新宣告

您無法重新宣告成員函式。 您可以定義它，但不能將它重新宣告。

## <a name="example"></a>範例

下列範例會產生 C2761。

```cpp
// C2761.cpp
class a {
   int t;
   void test();
};

void a::a;     // C2761
void a::test;  // C2761
```

## <a name="example"></a>範例

無法定義類別或結構的非靜態成員。  下列範例會產生 C2761。

```cpp
// C2761_b.cpp
// compile with: /c
struct C {
   int s;
   static int t;
};

int C::s;   // C2761
int C::t;   // OK
```

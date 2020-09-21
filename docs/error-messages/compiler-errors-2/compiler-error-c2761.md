---
title: 編譯器錯誤 C2761
ms.date: 11/04/2016
f1_keywords:
- C2761
helpviewer_keywords:
- C2761
ms.assetid: 38c79a05-b56d-485b-820f-95e8c0cb926f
ms.openlocfilehash: 7493934879068109c582a85592f485c1d391e2de
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743382"
---
# <a name="compiler-error-c2761"></a>編譯器錯誤 C2761

' function '：不允許成員函式的宣告

您無法重新宣告成員函式。 您可以定義它，但不能重新宣告它。

## <a name="examples"></a>範例

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

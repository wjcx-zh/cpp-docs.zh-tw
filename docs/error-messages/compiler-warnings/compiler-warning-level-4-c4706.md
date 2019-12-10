---
title: 編譯器警告 (層級 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: 2ff8794dcf29539b492f53bfdf6f0810988c0f72
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989914"
---
# <a name="compiler-warning-level-4-c4706"></a>編譯器警告 (層級 4) C4706

條件運算式中的指派

條件運算式中的測試值是指派的結果。

指派具有值（指派左邊的值），可在另一個運算式中以法律方式使用，包括測試運算式。

下列範例會產生 C4706：

```cpp
// C4706a.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a  = b ) // C4706
   {
   }
}
```

即使您在測試條件前後加上括弧，還是會發生警告：

```cpp
// C4706b.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a  =  b ) ) // C4706
   {
   }
}
```

如果您想要測試關聯性，而不是進行指派，請使用 `==` 運算子。 例如，下列程式程式碼會測試 a 和 b 是否相等：

```cpp
// C4706c.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( a == b )
   {
   }
}
```

如果您想要將測試值設為指派的結果，請進行測試以確保指派不是零或不是 null。 例如，下列程式碼不會產生這個警告：

```cpp
// C4706d.cpp
// compile with: /W4
int main()
{
   int a = 0, b = 0;
   if ( ( a = b ) != 0 )
   {
   }
}
```

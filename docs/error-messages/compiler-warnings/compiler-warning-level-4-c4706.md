---
title: 編譯器警告 (層級 4) C4706
ms.date: 11/04/2016
f1_keywords:
- C4706
helpviewer_keywords:
- C4706
ms.assetid: 89cd3f4f-812c-4a4b-9426-65a5a6d1b99c
ms.openlocfilehash: e57470fcd8e7b014084b094c9ca5e39f0a86d85e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395218"
---
# <a name="compiler-warning-level-4-c4706"></a>編譯器警告 (層級 4) C4706

條件運算式中使用指派運算子

條件運算式中的測試值已指派的結果。

指派有可用於另一個運算式，包括測試運算式的合法值 （值指派的左邊）。

下列範例會產生 C4706:

```
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

即使您按兩下測試條件前後的括號，就會發生此警告：

```
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

如果您想来測試關聯，而不進行指派，請使用`==`運算子。 例如下, 面這行測試是否與 b 相等：

```
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

如果您想要讓您的測試值指派的結果，測試以確保 指派為非零，或不是 null。 例如，下列程式碼將不會產生這個警告：

```
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
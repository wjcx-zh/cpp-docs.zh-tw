---
title: 編譯器警告 (層級 3) C4608
ms.date: 11/04/2016
f1_keywords:
- C4608
helpviewer_keywords:
- C4608
ms.assetid: 8b8f5f28-8ce9-457e-9d3d-a8c0efce9b6a
ms.openlocfilehash: 3599209043b877a60fbd7796959b8c9b76e1fb86
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188974"
---
# <a name="compiler-warning-level-3-c4608"></a>編譯器警告 (層級 3) C4608

'union_member' 已由初始設定式清單中的等位成員 'union_member' 初始化

初始化清單中相同等位的兩個成員已初始化。 您只能存取等位的一個成員。

下列範例會產生 C4608：

```cpp
// C4608.cpp
// compile with: /W3 /c
class X {
public:
   X(char c) : m_i( c + 1), m_c(c) {}   // C4608
   // try the following line instead
   // X(char c) : m_c(c) {}

private:
   union {
      int m_i;
      char m_c;
   };
};

union Y {
public:
   Y(char * name) : m_number(0.3), m_string( name ) {} // C4608

private:
   double m_number;
   char * m_string;
};
```
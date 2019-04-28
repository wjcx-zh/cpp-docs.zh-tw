---
title: 編譯器警告 (層級 1) C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: d35c4143d5b90c7a6a49337931dad4ba73804f20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221354"
---
# <a name="compiler-warning-level-1-c4621"></a>編譯器警告 (層級 1) C4621

任何的後置格式的 'operator--' 找到類型 'type'，改用前置格式

針對指定的型別定義沒有後置遞減運算子。 編譯器使用多載的前置運算子。

定義後置 `--` 運算子即可避免這個警告。 建立兩個引數版本`--`運算子，如下所示：

```
// C4621.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator--()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator--(int)
   // {
   //    A tmp = *this;
   //    m_nData -= 1;
   //    return tmp;
   // }

private:
   int m_nData;
};

int main()
{
   A a(10);
   --a;
   a--;   // C4621
}
```
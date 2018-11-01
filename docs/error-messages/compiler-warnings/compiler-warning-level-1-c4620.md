---
title: 編譯器警告 (層級 1) C4620
ms.date: 11/04/2016
f1_keywords:
- C4620
helpviewer_keywords:
- C4620
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
ms.openlocfilehash: 8e2d11d63704c86c824fd80e1c8a933c10e062d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532721"
---
# <a name="compiler-warning-level-1-c4620"></a>編譯器警告 (層級 1) C4620

找不到類型 'type' 後置格式的 'operator ++'，已改用前置格式

未定義指定類型的後置遞增運算子。 編譯器使用多載的前置運算子。

定義後置 `++` 運算子即可避免這個警告。 請如下所示建立 `++` 運算子的雙引數版本：

```
// C4620.cpp
// compile with: /W1
class A
{
public:
   A(int nData) : m_nData(nData)
   {
   }

   A operator++()
   {
      m_nData -= 1;
      return *this;
   }

   // A operator++(int)
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
   ++a;
   a++;   // C4620
}
```
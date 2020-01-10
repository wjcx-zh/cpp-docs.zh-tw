---
title: 編譯器警告（層級1） C4621
ms.date: 11/04/2016
f1_keywords:
- C4621
helpviewer_keywords:
- C4621
ms.assetid: 40931bd9-cb89-497e-86f0-cec9f016c63c
ms.openlocfilehash: 9dd4defe18a94f65e265d02f6c26c715667cd696
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052597"
---
# <a name="compiler-warning-level-1-c4621"></a>編譯器警告（層級1） C4621

找不到類型 ' type ' 的後置格式 ' operator--'，使用前置格式

針對指定的類型，沒有定義的後置遞減運算子。 編譯器使用多載的前置運算子。

定義後置 `--` 運算子即可避免這個警告。 建立 `--` 運算子的兩個引數版本，如下所示：

```cpp
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
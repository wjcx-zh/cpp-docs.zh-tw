---
title: 編譯器錯誤 C3852
ms.date: 11/04/2016
f1_keywords:
- C3852
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
ms.openlocfilehash: f264333d802967d0350caa8ab4ba4925ffe019af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754871"
---
# <a name="compiler-error-c3852"></a>編譯器錯誤 C3852

' member ' 具有類型 ' type '：匯總初始化無法初始化這個成員

嘗試將預設初始化做為匯總初始化的一部分，指派給無法在匯總初始化中接收預設初始化的資料成員。

下列範例會產生 C3852：

```cpp
// C3852.cpp
struct S
{
   short s;
};

struct S1
{
   int i;
   const S s;
};

struct S2
{
   int i;
   char & rc;
};

int main()
{
   S1 s1 = { 1 };   // C3852 const member
   // try the following line instead
   // S1 s1 = { 1, 2 };

   S2 s2 = { 2 };   // C3852 reference member
   // try the following line instead
   // char c = 'a';
   S2 s2 = { 2, c };
}
```

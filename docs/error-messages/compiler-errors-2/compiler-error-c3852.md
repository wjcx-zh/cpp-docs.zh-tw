---
title: 編譯器錯誤 C3852
ms.date: 11/04/2016
f1_keywords:
- C3852
helpviewer_keywords:
- C3852
ms.assetid: 194e5c5e-0dfb-414e-86db-791c11eb610c
ms.openlocfilehash: 4ad7718f4efbeb3b0bc481755fd239615ab796cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50450696"
---
# <a name="compiler-error-c3852"></a>編譯器錯誤 C3852

'member' 具有類型 'type': 彙總初始化無法初始化這個成員

您嘗試彙總的初始化過程中將無法在彙總初始化期間接收的預設值初始化的資料成員的預設初始化。

下列範例會產生 C3852:

```
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
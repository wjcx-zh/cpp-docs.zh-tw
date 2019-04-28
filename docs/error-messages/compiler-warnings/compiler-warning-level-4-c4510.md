---
title: 編譯器警告 (層級 4) C4510
ms.date: 11/04/2016
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 80183e9f7ef17cbc37592f36eb8db1df2be94827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221085"
---
# <a name="compiler-warning-level-4-c4510"></a>編譯器警告 (層級 4) C4510

'class': 無法產生預設建構函式

編譯器無法產生指定類別的預設建構函式，並沒有使用者定義的建構函式所建立。 您無法建立此類型的物件。

有幾種情況會使編譯器產生預設建構函式，包括：

- Const 資料成員。

- 資料成員的參考。

您要建立之類別的初始化這些成員的使用者定義的預設建構函式。

下列範例會產生 C4510:

```
// C4510.cpp
// compile with: /W4
struct A {
   const int i;
   int &j;
   A& operator=( const A& ); // C4510 expected
   // uncomment the following line to resolve this C4510
   // A(int ii, int &jj) : i(ii), j(jj) {}
};   // C4510

int main() {
}
```
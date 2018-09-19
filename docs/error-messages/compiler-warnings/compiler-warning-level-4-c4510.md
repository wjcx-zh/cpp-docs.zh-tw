---
title: 編譯器警告 （層級 4） C4510 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2aaf7286c2e900629a18d7df5824ef4b7af1f5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048964"
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
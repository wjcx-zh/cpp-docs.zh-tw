---
title: 編譯器警告（層級1） C4010
ms.date: 11/04/2016
f1_keywords:
- C4010
helpviewer_keywords:
- C4010
ms.assetid: d607a9ff-8f8f-45c0-b07b-3b2f439e5485
ms.openlocfilehash: 045b3f6e615e11c24caa9a088baf6ea9f6448efb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627323"
---
# <a name="compiler-warning-level-1-c4010"></a>編譯器警告（層級1） C4010

單行批註包含行接續字元

由//引進的單行批註包含以反斜線（\\）作為行接續字元。 編譯器會將下一行視為接續，並將它視為批註。

某些以語法為導向的編輯器並不會將接續字元後面的一行指定為批註。 忽略導致此警告的任何行的語法著色。

下列範例會產生 C4010：

```cpp
// C4010.cpp
// compile with: /WX
int main() {
   // the next line is also a comment because of the backslash \
   int a = 3; // C4010
   a++;
}
```
---
title: 編譯器警告 (層級 1) C4822
ms.date: 11/04/2016
f1_keywords:
- C4822
helpviewer_keywords:
- C4822
ms.assetid: 0f231a30-2eb0-4722-aaa0-e2d19d3e7eea
ms.openlocfilehash: 59c42227c7e8be9bd31c37776d9724d23db61837
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174865"
---
# <a name="compiler-warning-level-1-c4822"></a>編譯器警告 (層級 1) C4822

'member: 區域類別成員函式沒有主體

區域類別成員函式已宣告但未定義於類別中。 若要使用區域類別成員函式，您必須在類別中定義它。 您不能在類別中宣告它，但在類別外定義它。

區域類別成員函式的任何類別外定義會發生錯誤。

下列範例會產生 C4822：

```cpp
// C4822.cpp
// compile with: /W1
int main() {
   struct C {
      void func1(int);   // C4822
      // try the following line instead
      // void func1(int){}
  };
}
```

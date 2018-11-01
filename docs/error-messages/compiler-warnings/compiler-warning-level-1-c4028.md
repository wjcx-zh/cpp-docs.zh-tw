---
title: 編譯器警告 （層級 1） C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: bfe54fc40b4d6927a1d75f529ec9b619f9b29226
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490510"
---
# <a name="compiler-warning-level-1-c4028"></a>編譯器警告 （層級 1） C4028

型式參數 'number' 宣告不同

型式參數的型別不一致的宣告中的對應參數。 會使用原始宣告中的型別。

這個警告只適用於 C 原始程式碼。

## <a name="example"></a>範例

下列範例會產生 C4028。

```
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```
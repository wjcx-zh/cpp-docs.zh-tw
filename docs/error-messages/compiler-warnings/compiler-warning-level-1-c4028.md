---
title: 編譯器警告（層級1） C4028
ms.date: 11/04/2016
f1_keywords:
- C4028
helpviewer_keywords:
- C4028
ms.assetid: c3e8b70b-e870-416c-a285-bba5f71dbfc6
ms.openlocfilehash: 19bfd2659ee9017d3a304dee2d647da091515876
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623844"
---
# <a name="compiler-warning-level-1-c4028"></a>編譯器警告（層級1） C4028

型式參數 ' number ' 與宣告不同

型式參數的類型不會與宣告中的對應參數一致。 使用原始宣告中的類型。

此警告僅適用于 C 原始程式碼。

## <a name="example"></a>範例

下列範例會產生 C4028。

```c
// C4028.c
// compile with: /W1 /Za
void f(int , ...);
void f(int i, int j) {}   // C4028

void g(int , int);
void g(int i, int j) {}   // OK

int main() {}
```
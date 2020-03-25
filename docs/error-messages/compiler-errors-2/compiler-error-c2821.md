---
title: 編譯器錯誤 C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: d099c4a0f6e1ea77a25213e3873b8a0814e28dcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201991"
---
# <a name="compiler-error-c2821"></a>編譯器錯誤 C2821

' operator new ' 的第一個型式參數必須是 ' 不帶正負號的 int '

[Operator new](../../standard-library/new-operators.md#op_new)的第一個型式參數必須是不帶正負號的 `int`。

## <a name="example"></a>範例

下列範例會產生 C2821：

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```

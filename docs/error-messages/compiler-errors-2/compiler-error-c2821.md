---
title: 編譯器錯誤 C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: 115874724a24530e0d85256e11c3aa355aa4d6af
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225393"
---
# <a name="compiler-error-c2821"></a>編譯器錯誤 C2821

' operator new ' 的第一個型式參數必須是 ' 不帶正負號的 int '

[Operator new](../../standard-library/new-operators.md#op_new)的第一個型式參數必須是不帶正負號的 **`int`** 。

## <a name="example"></a>範例

下列範例會產生 C2821：

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```

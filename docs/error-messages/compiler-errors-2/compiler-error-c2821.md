---
title: 編譯器錯誤 C2821
ms.date: 11/04/2016
f1_keywords:
- C2821
helpviewer_keywords:
- C2821
ms.assetid: e8d71988-a968-4484-94db-e8c3bad74a4a
ms.openlocfilehash: 5c725d9648a7800c68a2fbff20e594a400c296c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632541"
---
# <a name="compiler-error-c2821"></a>編譯器錯誤 C2821

'operator new' 的第一個型式參數必須是 'unsigned 的 int'

第一個正式參數[new 運算子](../../standard-library/new-operators.md#op_new)必須是不帶正負號`int`。

## <a name="example"></a>範例

下列範例會產生 C2821:

```cpp
// C2821.cpp
// compile with: /c
void * operator new( /* unsigned int,*/ void * );   // C2821
void * operator new( unsigned int, void * );
```
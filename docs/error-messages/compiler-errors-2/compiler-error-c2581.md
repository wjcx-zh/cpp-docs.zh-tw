---
title: 編譯器錯誤 C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: a632d6a47afb29b8bb46761c3188391905eda842
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87206870"
---
# <a name="compiler-error-c2581"></a>編譯器錯誤 C2581

' type '：靜態 ' operator = ' 函數不合法

指派（ `=` ）運算子不正確地宣告為 **`static`** 。 指派運算子不可以是 **`static`** 。 如需詳細資訊，請參閱[使用者定義的運算子（c + +/cli）](../../dotnet/user-defined-operators-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C2581。

```cpp
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```

---
title: 編譯器錯誤 C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: 03fc7e9da8a9b3a2e2c445f5b06395c2616f0d98
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755430"
---
# <a name="compiler-error-c2581"></a>編譯器錯誤 C2581

' type '：靜態 ' operator = ' 函數不合法

指派（`=`）運算子不正確地宣告為 `static`。 無法 `static`指派運算子。 如需詳細資訊，請參閱[使用者定義的C++運算子（/cli）](../../dotnet/user-defined-operators-cpp-cli.md)。

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

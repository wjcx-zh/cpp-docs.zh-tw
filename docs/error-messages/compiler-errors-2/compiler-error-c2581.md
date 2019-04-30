---
title: 編譯器錯誤 C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: edfab092c82f9dc1d4b9dfe5d21daa2b2ab98d08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385858"
---
# <a name="compiler-error-c2581"></a>編譯器錯誤 C2581

'type': 靜態 ' 運算子 =' 函式不合法

指派 (`=`) 運算子不正確地宣告為`static`。 指派運算子不能`static`。 如需詳細資訊，請參閱 <<c0> [ 使用者定義的運算子 (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md)。</c0>

## <a name="example"></a>範例

下列範例會產生 C2581。

```
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```
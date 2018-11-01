---
title: 編譯器錯誤 C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: ac9afdfc11a13dd667b06289c73332593a4d884e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456351"
---
# <a name="compiler-error-c3076"></a>編譯器錯誤 C3076

'instance': 您無法將執行個體的參考類型 'type'，內嵌在原生類型

原生類型不能包含 CLR 型別的執行個體。

如需詳細資訊，請參閱 <<c0> [ 參考類型的 c + + 堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3076。

```
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```
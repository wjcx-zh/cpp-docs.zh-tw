---
title: 編譯器警告 (層級 3) C4636
ms.date: 11/04/2016
f1_keywords:
- C4636
helpviewer_keywords:
- C4636
ms.assetid: 59112a0f-850f-41c6-bd84-8ae8dc84706a
ms.openlocfilehash: 7327189a61e2545bb6003cd95e1ddb116f9f7c94
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542229"
---
# <a name="compiler-warning-level-3-c4636"></a>編譯器警告 (層級 3) C4636

套用至 'construct' 的 XML 文件註解: 標記必須是非空白的 '' 屬性。

標記 (如 `cref`) 沒有值。

## <a name="example"></a>範例

下列範例會產生 C4636。

```
// C4636.cpp
// compile with: /clr /doc /W3 /c
/// <see cref=''/>
// /// <see cref='System::Exception'/>
ref struct A {   // C4636
   void f(int);
};

// OK
/// <see cref='System::Exception'/>
ref struct B {
   void f(int);
};
```
---
title: 編譯器警告 (層級 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518478"
---
# <a name="compiler-warning-level-4-c4690"></a>編譯器警告 (層級 4) C4690

> \[ emitidl (pop)]: pop 數目比 push

## <a name="remarks"></a>備註

[emitidl](../../windows/emitidl.md) 屬性的 pop 作業比 push 作業多一次。

## <a name="example"></a>範例

下列範例會產生 C4690。 若要修正此問題，請確定屬性則會彈出會推入的次數相同。

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```

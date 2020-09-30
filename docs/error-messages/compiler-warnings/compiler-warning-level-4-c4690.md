---
title: 編譯器警告 (層級 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: de996128c68ebf96b4a00f6206cbaf54d97ca275
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91509973"
---
# <a name="compiler-warning-level-4-c4690"></a>編譯器警告 (層級 4) C4690

> \[ emitidl ( pop ) ]：多個 pop 超過推播

## <a name="remarks"></a>備註

[emitidl](../../windows/attributes/emitidl.md) 屬性的 pop 作業比 push 作業多一次。

## <a name="example"></a>範例

下列範例會產生 C4690。 若要修正此問題，請確定屬性已在推送時，完全依照多次快顯。

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```

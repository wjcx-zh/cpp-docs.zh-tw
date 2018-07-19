---
title: 編譯器警告 （層級 4） C4690 |Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4690
dev_langs:
- C++
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04fb68bdab762f0f541849fad1568caff836b623
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853318"
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

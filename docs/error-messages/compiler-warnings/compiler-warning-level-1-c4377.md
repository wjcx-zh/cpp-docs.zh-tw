---
title: 編譯器警告（層級1） C4377
ms.date: 11/04/2016
f1_keywords:
- C4377
helpviewer_keywords:
- C4377
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
ms.openlocfilehash: 30e2ecb1d5e0de290c028cdfb53c7df831a732b4
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966454"
---
# <a name="compiler-warning-level-1-c4377"></a>編譯器警告（層級1） C4377

原生類型預設為私用;-d1PrivateNativeTypes 已被取代

在舊版中，元件中的原生類型預設為公用，並使用內部未記載的編譯器選項（ **/d1PrivateNativeTypes**）將其設為私用。

在元件中，所有類型（原生和 CLR）現在都是私用的，因此不再需要 **/d1PrivateNativeTypes** 。

## <a name="example"></a>範例

下列範例會產生 C4377。

```cpp
// C4377.cpp
// compile with: /clr /d1PrivateNativeTypes /W1
// C4377 warning expected
int main() {}
```
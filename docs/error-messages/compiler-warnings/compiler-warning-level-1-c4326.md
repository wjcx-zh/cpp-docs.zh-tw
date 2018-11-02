---
title: 編譯器警告 (層級 1) C4326
ms.date: 08/27/2018
f1_keywords:
- C4326
helpviewer_keywords:
- C4326
ms.assetid: d44d2c4e-9456-42d3-b35b-4ba4b2d42ec7
ms.openlocfilehash: d14a1902db4dcf2224ce6a58db120a81ebb5620f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50601158"
---
# <a name="compiler-warning-level-1-c4326"></a>編譯器警告 (層級 1) C4326

> 傳回的類型 '*函式*'應該是'*type1*' 而不是 '*type2*'

## <a name="remarks"></a>備註

函式傳回的型別以外*type1*。 例如，使用[/Za](../../build/reference/za-ze-disable-language-extensions.md)，**主要**未傳回**int**。

## <a name="example"></a>範例

下列範例會產生 C4326，並示範如何修正此問題：

```cpp
// C4326.cpp
// compile with: /Za /W1
char main()
{
    // C4326, instead use int main()
}
```
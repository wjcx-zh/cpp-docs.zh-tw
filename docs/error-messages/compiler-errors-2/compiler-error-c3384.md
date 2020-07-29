---
title: 編譯器錯誤 C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: fdc129be94fce3f97eca988d8080e9d01fd48248
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221090"
---
# <a name="compiler-error-c3384"></a>編譯器錯誤 C3384

'type_parameter': 數值條件約束和 ref 條件約束互斥

您不能將泛型型別限制為 **`value class`** 和 **`ref class`** 。

如需詳細資訊，請參閱[泛型型別參數的條件約束（c + +/cli）](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 。

## <a name="example"></a>範例

下列範例會產生 C3384。

```cpp
// C3384.cpp
// compile with: /c /clr
generic <typename T>
where T : ref class
where T : value class   // C3384
ref class List {};
```

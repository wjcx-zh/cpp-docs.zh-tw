---
title: 編譯器錯誤 C3384
ms.date: 11/04/2016
f1_keywords:
- C3384
helpviewer_keywords:
- C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
ms.openlocfilehash: 059518462bd7a0463fd03fec6434acbbda7ee60a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756431"
---
# <a name="compiler-error-c3384"></a>編譯器錯誤 C3384

'type_parameter': 數值條件約束和 ref 條件約束互斥

您不能將泛型類型限制為 `value class` 和 `ref class`。

如需詳細資訊，請參閱[泛型型別參數（C++/Cli）的條件約束](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

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

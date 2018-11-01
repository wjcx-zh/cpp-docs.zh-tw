---
title: 編譯器錯誤 C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: 70d23e22780b6efc8220675655d8ed095ca50bab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50557374"
---
# <a name="compiler-error-c3400"></a>編譯器錯誤 C3400

循環條件約束相依性，涉及 'constraint_1' 和 'constraint_2'

編譯器偵測到循環條件約束。

如需詳細資訊，請參閱 <<c0> [ 泛型類型參數的條件約束 (C + + /cli CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3400。

```
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```
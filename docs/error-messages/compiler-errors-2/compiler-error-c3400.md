---
title: 編譯器錯誤 C3400
ms.date: 11/04/2016
f1_keywords:
- C3400
helpviewer_keywords:
- C3400
ms.assetid: d44169a8-73b6-4766-b406-b3a6c93f2a4d
ms.openlocfilehash: cb4b9d03e10155383f2c58cca07253ae69c2c69a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737500"
---
# <a name="compiler-error-c3400"></a>編譯器錯誤 C3400

循環條件約束相依性，涉及 'constraint_1' 和 'constraint_2'

編譯器偵測到循環條件約束。

如需詳細資訊，請參閱[泛型型別參數的限制式 (C++/CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C3400。

```cpp
// C3400.cpp
// compile with: /clr /c
generic<class T, class U>
where T : U
where U : T   // C3400
public ref struct R {};
```

---
title: 編譯器錯誤 C3669
ms.date: 11/04/2016
f1_keywords:
- C3669
helpviewer_keywords:
- C3669
ms.assetid: be9c7ae4-e96f-47ab-922a-39a3537d5ca6
ms.openlocfilehash: 560f4e8ef39e265f20d3c119858ff06b463d9841
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758134"
---
# <a name="compiler-error-c3669"></a>編譯器錯誤 C3669

' member '：在靜態成員函式或函式上不允許有覆寫規範 ' override '

指定了不正確的覆寫。 如需詳細資訊，請參閱[明確覆寫](../../extensions/explicit-overrides-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3669。

```cpp
// C3669.cpp
// compile with: /clr
public ref struct R {
   R() override {}   // C3669
};
```

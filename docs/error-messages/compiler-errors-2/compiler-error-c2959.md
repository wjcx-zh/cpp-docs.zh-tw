---
title: 編譯器錯誤 C2959
ms.date: 11/04/2016
f1_keywords:
- C2959
helpviewer_keywords:
- C2959
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
ms.openlocfilehash: 3465c3275783a625c172b711e9c41789b6f36713
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777454"
---
# <a name="compiler-error-c2959"></a>編譯器錯誤 C2959

泛型類別或函式可能不是樣板的成員

如需詳細資訊，請參閱 < [Windows 執行階段和 Managed 樣板](../../extensions/windows-runtime-and-managed-templates-cpp-component-extensions.md)並[泛型](../../extensions/generics-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C2959。

```
// C2959.cpp
// compile with: /clr /c
template <class T> ref struct S {
   generic <class U> ref struct GR1;   // C2959
};
```
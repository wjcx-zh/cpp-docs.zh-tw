---
title: 編譯器錯誤 C2364
ms.date: 11/04/2016
f1_keywords:
- C2364
helpviewer_keywords:
- C2364
ms.assetid: 4f550571-94b5-42ca-84cb-663fecbead44
ms.openlocfilehash: fb019d729bc100296742b15ba95460fe0e404673
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759876"
---
# <a name="compiler-error-c2364"></a>編譯器錯誤 C2364

' type '：自訂屬性的類型不合法

自訂屬性的具名引數僅限於編譯時間常數。 例如，整數類資料類型（int、char 等等）、System：： Type ^ 和 System：： Object ^。

## <a name="example"></a>範例

下列範例會產生 C2364。

```cpp
// c2364.cpp
// compile with: /clr /c
using namespace System;

[attribute(AttributeTargets::All)]
public ref struct ABC {
public:
   // Delete the following line to resolve.
   ABC( Enum^ ) {}   // C2364
   ABC( int ) {}   // OK
};
```

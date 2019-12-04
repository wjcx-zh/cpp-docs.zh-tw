---
title: 編譯器錯誤 C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: f3ce849113b0fc21a192f748bc46fc35be48880d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749629"
---
# <a name="compiler-error-c3076"></a>編譯器錯誤 C3076

' instance '：您無法在原生類型中內嵌參考型別 ' type ' 的實例

原生類型不能包含 CLR 類型的實例。

如需詳細資訊，請參閱[ C++參考型別的堆疊語義](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3076。

```cpp
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```

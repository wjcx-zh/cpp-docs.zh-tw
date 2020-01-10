---
title: 編譯器錯誤 C2261
ms.date: 11/04/2016
f1_keywords:
- C2261
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
ms.openlocfilehash: f23c2a38f8e4d6781af73fb70a25cf4737e2c4e8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758771"
---
# <a name="compiler-error-c2261"></a>編譯器錯誤 C2261

' string '：元件參考無效，無法解析

值無效。

<xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> 用來指定 friend 元件。 例如，如果 .dll 想要指定 b. .dll 做為 friend 元件，您會指定（在 .dll 中）： InternalsVisibleTo （"b"）。 然後執行時間會允許 b. 存取 .dll 中的所有專案（私用類型除外）。

如需指定 friend 元件時的正確語法詳細資訊，請參閱[FriendC++元件（）](../../dotnet/friend-assemblies-cpp.md)。

## <a name="example"></a>範例

下列範例會產生 C2261。

```cpp
// C2261.cpp
// compile with: /clr /c
using namespace System::Runtime::CompilerServices;
[assembly: InternalsVisibleTo("a,a,a")];   // C2261
[assembly: InternalsVisibleTo("a.a")];   // OK
[assembly: InternalsVisibleTo("a")];   // OK
```

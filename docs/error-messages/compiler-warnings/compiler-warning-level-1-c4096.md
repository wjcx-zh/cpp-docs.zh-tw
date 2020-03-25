---
title: 編譯器警告（層級1） C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 4f5a45339673b57f946f206e1eaff0d23ec6fee9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163932"
---
# <a name="compiler-warning-level-1-c4096"></a>編譯器警告（層級1） C4096

' a '：介面不是 COM 介面;將不會發出至 IDL

您可能想要做為 COM 介面的介面定義未定義為 COM 介面，因此不會發出至 IDL 檔案。

如需指出介面為 COM 介面的清單屬性，請參閱[介面屬性](../../windows/attributes/interface-attributes.md)。

下列範例會產生 C4096：

```cpp
// C4096.cpp
// compile with: /W1 /LD
#include "windows.h"
[module(name="xx")];

// [object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct b : a
{
};   // C4096, remove coclass or uncomment object
```

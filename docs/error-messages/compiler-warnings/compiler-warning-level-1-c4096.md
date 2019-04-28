---
title: 編譯器警告 （層級 1） C4096
ms.date: 11/04/2016
f1_keywords:
- C4096
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
ms.openlocfilehash: 287465e9a3f5681f459f0823a4409b0906309a55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62280452"
---
# <a name="compiler-warning-level-1-c4096"></a>編譯器警告 （層級 1） C4096

'a': 介面不是 COM 介面;將不會發出到 IDL

您可能想為 COM 介面的介面定義未定義為 COM 介面，並因此將不會被發出到 IDL 檔案。

請參閱[介面屬性](../../windows/attributes/interface-attributes.md)的屬性清單，表示介面的 COM 介面。

下列範例會產生 C4096:

```
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
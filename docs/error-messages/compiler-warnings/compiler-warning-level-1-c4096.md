---
title: 編譯器警告 （層級 1） C4096 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2aaf3f37e9699547c3a85c55a2f72d4baab7a6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047690"
---
# <a name="compiler-warning-level-1-c4096"></a>編譯器警告 （層級 1） C4096

'a': 介面不是 COM 介面;將不會發出到 IDL

您可能想為 COM 介面的介面定義未定義為 COM 介面，並因此將不會被發出到 IDL 檔案。

請參閱[介面屬性](../../windows/interface-attributes.md)的屬性清單，表示介面的 COM 介面。

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
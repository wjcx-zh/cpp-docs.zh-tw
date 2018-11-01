---
title: 編譯器錯誤 C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: c23f17483925f25468214165fb459db577e576fc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50475084"
---
# <a name="compiler-error-c2006"></a>編譯器錯誤 C2006

'directive' 必須是檔案名稱，找到 'token'

指示詞，例如[#include](../../preprocessor/hash-include-directive-c-cpp.md)或是[#import](../../preprocessor/hash-import-directive-cpp.md)需要檔案名稱。 若要解決此錯誤，請確定*語彙基元*是有效的檔名。 此外，將檔案名稱放在雙引號或角括弧。

下列範例會產生 C2006:

```
// C2006.cpp
#include stdio.h   // C2006
```

可能的解決方式：

```
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```
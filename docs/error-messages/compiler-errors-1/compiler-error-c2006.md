---
title: 編譯器錯誤 C2006 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e9468be17584a54047563bace2b35f5cb4888b41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031199"
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
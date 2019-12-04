---
title: 編譯器錯誤 C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756548"
---
# <a name="compiler-error-c2006"></a>編譯器錯誤 C2006

' 指示詞 ' 必須是檔案名，但找到 ' token '

[#Include](../../preprocessor/hash-include-directive-c-cpp.md)或[#import](../../preprocessor/hash-import-directive-cpp.md)等指示詞需要檔案名。 若要解決此錯誤，請確定*token*是有效的檔案名。 此外，請以雙引號或角括弧括住檔案名。

下列範例會產生 C2006：

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

可能的解決方案：

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```

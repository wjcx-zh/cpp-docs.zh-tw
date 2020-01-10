---
title: 編譯器錯誤 C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 6c7e941970415c933b38f35b6c09247a3c0fd411
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757393"
---
# <a name="compiler-error-c2014"></a>編譯器錯誤 C2014

預處理器命令必須以第一個非空白字元空間的形式啟動

預處理器指示詞的 `#` 正負號必須是不是空白字元之行的第一個字元。

下列範例會產生 C2014：

```cpp
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

可能的解決方案：

```cpp
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```

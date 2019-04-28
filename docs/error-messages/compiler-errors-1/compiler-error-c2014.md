---
title: 編譯器錯誤 C2014
ms.date: 11/04/2016
f1_keywords:
- C2014
helpviewer_keywords:
- C2014
ms.assetid: 231d8e9c-48c0-4027-99a3-245d186275ec
ms.openlocfilehash: 58cf9867a9e36b304ab9da79084bc01dff453892
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350698"
---
# <a name="compiler-error-c2014"></a>編譯器錯誤 C2014

前置處理器命令必須以第一個有非空白的啟動

`#`正負號的前置處理器指示詞必須是不是空白的該行的第一個字元。

下列範例會產生 C2014:

```
// C2014.cpp
int k; #include <stdio.h>   // C2014
```

可能的解決方式：

```
// C2014b.cpp
// compile with: /c
int k;
#include <stdio.h>
```
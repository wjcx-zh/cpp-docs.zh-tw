---
title: 編譯器警告 （層級 4） C4233 |Microsoft 文件
ms.custom: ''
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4233
dev_langs:
- C++
helpviewer_keywords:
- C4233
ms.assetid: 9aa51fc6-8ef3-43b5-bafb-c9333cf60de3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a933d41fd8e7cf3b94e458efff72193b8ce5e187
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4233"></a>編譯器警告 (層級 4) C4233

> 使用非標準擴充: '*關鍵字*' 關鍵字在 c + +，不是 C 中才支援

編譯器將編譯為 C，而不是 c + +，您的原始程式碼，而且您使用的關鍵字，在 c + + 中才有效。 編譯器會編譯為 C 原始程式檔如果來源檔案的副檔名為.c 或您使用[/Tc](../../build/reference/tc-tp-tc-tp-specify-source-file-type.md)。

這個警告會自動升級為錯誤。 如果您想要修改此行為，使用[#pragma 警告](../../preprocessor/warning.md)。 比方說，若要將層級 4 警告問題 c4233，將這一行加入至您的原始程式碼檔：

```cpp
#pragma warning(4:4233)
```

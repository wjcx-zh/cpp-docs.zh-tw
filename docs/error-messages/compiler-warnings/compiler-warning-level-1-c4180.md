---
title: 編譯器警告 （層級 1） C4180 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4180
dev_langs:
- C++
helpviewer_keywords:
- C4180
ms.assetid: 40c91bd4-37f1-4d59-a4f3-d5ddab68239b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 231c979c0c728e3a69ec27905e7fbd42342bbd6d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080047"
---
# <a name="compiler-warning-level-1-c4180"></a>編譯器警告 (層級 1) C4180

套用至函式類型的限定詞沒有意義; 已忽略

限定詞 (例如 **const**) 套用至 `typedef`所定義的函式類型。

## <a name="example"></a>範例

```
// C4180.cpp
// compile with: /W1 /c
typedef int FuncType(void);

// the const qualifier cannot be applied to the
// function type FuncType
const FuncType f;   // C4180
```
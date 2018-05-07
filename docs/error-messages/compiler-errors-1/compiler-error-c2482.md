---
title: 編譯器錯誤 C2482 |Microsoft 文件
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2482
dev_langs:
- C++
helpviewer_keywords:
- C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2c4725dd357854db504272e5b8b9d88641b143d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2482"></a>編譯器錯誤 C2482

>'*識別碼*': 'thread' 不允許的資料的動態初始化

這則錯誤訊息是在 Visual Studio 2015 和更新版本已過時。 在舊版中，變數宣告可透過`thread`需要執行階段評估的運算式來初始化屬性。 靜態運算式，才能初始化`thread`資料。

## <a name="example"></a>範例

下列範例會產生 C2482 在 Visual Studio 2013 及更早版本：

```cpp
// C2482.cpp
// compile with: /c
#define Thread __declspec( thread )
Thread int tls_i = tls_i;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i = sizeof( tls_i );   // Okay in C and C++
```

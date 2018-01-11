---
title: "編譯器錯誤 C2482 |Microsoft 文件"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2482
dev_langs: C++
helpviewer_keywords: C2482
ms.assetid: 98c87da2-625c-4cc2-9bf7-78d15921e779
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c4a5d081e7a19f09f10e40e3799f724f44b295fc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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

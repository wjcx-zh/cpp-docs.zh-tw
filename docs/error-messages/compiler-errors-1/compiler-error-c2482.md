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
ms.openlocfilehash: c3dd23069f389d0a02e10d26edb7ee4fd3c373cb
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2018
---
# <a name="compiler-error-c2482"></a>編譯器錯誤 C2482

>'*識別碼*': managed WinRT 程式碼中不允許 'thread' 資料的動態初始化

## <a name="remarks"></a>備註

在 managed 或 WinRT 程式碼的變數宣告可透過[__declspec （thread)](../../cpp/thread.md)儲存類別修飾詞屬性或[thread_local](../../cpp/storage-classes-cpp.md#thread_local)無法以運算式初始化的儲存類別規範需要在執行階段評估。 靜態運算式，才能初始化`__declspec(thread)`或`thread_local`這些執行階段環境中的資料。

## <a name="example"></a>範例

下列範例會產生 C2482 管理增益集 (**/clr**) 和 WinRT (**/ZW**) 程式碼：

```cpp
// C2482.cpp
// For managed example, compile with: cl /EHsc /c /clr C2482.cpp
// For WinRT example, compile with: cl /EHsc /c /ZW C2482.cpp
#define Thread __declspec( thread )
Thread int tls_i1 = tls_i1;   // C2482

int j = j;   // OK in C++; C error
Thread int tls_i2 = sizeof( tls_i2 );   // Okay in C and C++
```

若要修正此問題，請使用常數時，初始化執行緒區域儲存區**constexpr**，或靜態的運算式。 分別執行任何執行緒專屬的初始化。
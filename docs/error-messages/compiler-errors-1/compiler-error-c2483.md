---
title: "編譯器錯誤 C2483 |Microsoft 文件"
ms.custom: 
ms.date: 09/15/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2483
dev_langs: C++
helpviewer_keywords: C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5f7f9f30724c02d44e054bf16ff1460370c30e06
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2483"></a>編譯器錯誤 C2483

>'*識別碼*': 建構函式或解構函式的物件不可以宣告為 '執行緒'

這則錯誤訊息是在 Visual Studio 2015 和更新版本已過時。 在舊版中，變數宣告與`thread`屬性無法使用建構函式或其他需要執行階段評估的運算式來初始化。 靜態運算式，才能初始化`thread`資料。

## <a name="example"></a>範例

下列範例會在 Visual Studio 2013 和舊版中產生 C2483。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error  

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>請參閱

[thread](../../cpp/thread.md)
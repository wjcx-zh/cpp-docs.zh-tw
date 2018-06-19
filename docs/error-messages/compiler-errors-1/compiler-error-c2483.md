---
title: 編譯器錯誤 C2483 |Microsoft 文件
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a10fd33ebeef43904db964fc327fb749029f963
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197971"
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

## <a name="see-also"></a>另請參閱

[thread](../../cpp/thread.md)
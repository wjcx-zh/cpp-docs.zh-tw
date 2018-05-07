---
title: 編譯器錯誤 C3156 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3156
dev_langs:
- C++
helpviewer_keywords:
- C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9557043bac056435dd53b210359e7bb72b29b6d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3156"></a>編譯器錯誤 C3156
'class'：您無法具有一個 managed 或 WinRT 類型的本機定義  
  
 函式不可包含 managed 或 WinRT 類別、結構或介面的定義或宣告。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3156。  
  
```  
// C3156.cpp  
// compile with: /clr /c  
void f() {  
   ref class X {};   // C3156  
   ref class Y;   // C3156  
}  
```  

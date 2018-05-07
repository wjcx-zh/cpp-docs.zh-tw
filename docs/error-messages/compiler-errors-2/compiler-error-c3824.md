---
title: 編譯器錯誤 C3824 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3824
dev_langs:
- C++
helpviewer_keywords:
- C3824
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e5202ff0236fca8d14c87bd55f1d314baa6bb2a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3824"></a>編譯器錯誤 C3824
'member': 這個類型不能出現在此內容 （函式參數、 傳回型別或靜態成員）  
  
 Pin 指標不可以是函式參數、 傳回型別，或宣告`static`。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3824:  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  

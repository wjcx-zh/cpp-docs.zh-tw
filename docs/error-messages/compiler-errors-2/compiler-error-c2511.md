---
title: 編譯器錯誤 C2511 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2511
dev_langs:
- C++
helpviewer_keywords:
- C2511
ms.assetid: df999efe-fe2b-418b-bb55-4af6a0592631
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d97cbbd75d3b39b55ff640ed99e261ba349043d3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33199624"
---
# <a name="compiler-error-c2511"></a>編譯器錯誤 C2511
'identifier': 多載 'class' 中找不到的成員函式  
  
 使用指定的參數宣告的函式沒有版本。  可能的原因：  
  
1.  錯誤的參數傳遞至函式。  
  
2.  傳遞的參數順序錯誤。  
  
3.  參數名稱的拼字錯誤。  
  
 下列範例會產生 C2511:  
  
```  
// C2511.cpp  
// compile with: /c  
class C {  
   int c_2;  
   int Func(char *, char *);  
};  
  
int C::Func(char *, char *, int i) {   // C2511  
// try the following line instead  
// int C::Func(char *, char *) {  
   return 0;  
}  
```